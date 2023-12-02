# Nether Portal
Deploy your obsidian vault using MkDocs.

## Project Structure

```mermaid
graph TD
    a[Push vault]

    a--CI/CD-->b

    subgraph b[Preprocessor]
        b1[Prepares .md files for mkdocs]
    end

    b-->c

    subgraph c[Wrapper]
        c1[Moves .md files into mkdocs repo]
    end

    c--git push-->d

    d[Publish on GitHub Pages]
```

## Platform
Github actions

## Preprocessor
- preprocess PDFs
    - Add `Name (PDF).md` for every `Name.pdf`
- preprocess equations
    - remove whitespace
    - remove equation numbers
    - Add blank lines around every block
- preprocess admonitions (callouts)
    - Fix syntax
    - Map admonition type names
- preprocess file names
    - Add `# Filename` to the top of every file
- preprocess obsidian links
    - (low priority)

## Wrapper
- retrieve template mkdocs tree
- move preprocessed vault into `docs/`
- commit changes
- mkdocs gh-deploy (handled by pages repo)

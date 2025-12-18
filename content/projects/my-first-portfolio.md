+++
date = '2025-12-18T16:06:29Z'
draft = false
title = 'My First Portfolio'
+++



A basic Hugo portfolio site takes about 15–30 minutes to stand up from scratch using the CLI and git.

## 1. Install prerequisites

- Install Hugo (extended) using your OS package manager (for example on macOS: `brew install hugo`).
- Confirm it works: `hugo version` should print the installed version.
- Install Git if you do not already have it, and verify with `git --version`.

## 2. Scaffold a new Hugo site

Run these in a parent “projects” directory:

```bash
hugo new site my-portfolio
cd my-portfolio
```

This creates the Hugo directory structure in `my-portfolio` (config file, `content`, `layouts`, `static`, etc.).

## 3. Initialize a git repository

Inside `my-portfolio`:

```bash
git init
git add .
git commit -m "Initial Hugo site scaffold"
```

This creates an empty git repo, stages the generated files, and records the first commit.

If you want to connect to GitHub:

```bash
git remote add origin git@github.com:usmc6312-stack/my-jam.git
git branch -M main
git push -u origin main   # or 'master' depending on your default branch
```

## 4. Add a simple portfolio theme

Use a starter theme that is easy to customize, for example Ananke (good generic starter) or a dedicated portfolio theme.
From the site root:

```bash
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo "theme = 'ananke'" >> hugo.toml
git add .
git commit -m "Add Ananke theme"
```

`git submodule add` tracks the theme as a git submodule so it stays versioned with your repo.

For a portfolio-focused look, you can later swap to a portfolio theme from the Hugo themes gallery (for example those under the “Portfolio” category).

## 4.1 Serve it up

```bash
hugo serve
```

## 5. Add basic portfolio content

Create a homepage section, an about page, and at least one project entry:

```bash
hugo new _index.md
hugo new about/_index.md
hugo new projects/my-first-project.md
```

These commands create content files in the `content` directory with front matter ready to edit.

Open the new Markdown files and update front matter and text, for example in `content/projects/my-first-project.md`:

```yaml
---
title: "My First Project"
date: 2025-12-18
draft: false
tags: ["go", "devops"]
---
Short description of what this project is, what problem it solves, and your role.
```

Mark `draft: false` for anything you want visible on the live site.

Then commit:

```bash
git add content
git commit -m "Add initial portfolio content"
```

## 6. Run the local dev server

From the site root:

```bash
hugo server
```

Open the URL shown in the terminal (usually `http://localhost:1313/`) to view the site.
Leave the server running while you edit content; changes appear on refresh or live reload.

## 6.1 Add content

```bash
hugo new content content/posts/my-first-post.md
```

## 6.2 Updat the content

```
+++
title = 'My First Post'
date = 2024-01-14T07:07:07+01:00
draft = true
+++
```

## 7. Build static files for deployment

When you are ready to deploy:

```bash
hugo
```

This generates a `public` directory containing all static HTML, CSS, and assets.
Commit any configuration or content changes (but usually ignore `public` if deploying via CI) and push to your remote:

```bash
git add .
git commit -m "Prepare for initial deployment"
git push
```

# Agency AI

A responsive, single-page digital agency website built with React, Vite, and Tailwind CSS v4.  
It showcases services, portfolio work, team members, and a contact form with animated UI interactions and dark mode support.

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss&logoColor=white)
![License](https://img.shields.io/badge/License-Not%20Specified-lightgrey)

## Table of Contents

- [Overview](#overview)
- [Problem It Solves](#problem-it-solves)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Screenshots / Preview](#screenshots--preview)
- [Demo / Links](#demo--links)
- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [Running the Project Locally](#running-the-project-locally)
- [Available Scripts](#available-scripts)
- [API / External Integrations](#api--external-integrations)
- [Usage Guide](#usage-guide)
- [Example Workflow](#example-workflow)
- [Folder Structure](#folder-structure)
- [Configuration Notes](#configuration-notes)
- [Deployment](#deployment)
- [Testing](#testing)
- [Performance, Accessibility, SEO](#performance-accessibility-seo)
- [Security Notes](#security-notes)
- [Roadmap](#roadmap)
- [Known Limitations](#known-limitations)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

## Overview

Agency AI is a frontend portfolio/landing page template for a marketing or digital agency brand.  
The app is a single-page layout with section-based navigation and polished motion effects across hero, services, work cards, team, and contact form.

## Problem It Solves

This project provides a ready-to-customize agency website that helps you:

- Launch a modern web presence quickly
- Showcase services and portfolio work in one page
- Capture inquiries through a contact form without building a backend
- Present a recruiter/client-friendly frontend codebase using current React tooling

## Key Features

- Responsive single-page layout
- Sticky navbar with mobile sidebar menu
- Light/Dark mode toggle with `localStorage` persistence
- Animated section reveals and card interactions using Motion
- Custom cursor dot + ring effect
- Services and work showcase cards
- Team grid section
- Contact form integrated with Web3Forms
- Toast notifications for form submission feedback
- Tailwind CSS v4 styling with custom theme color

## Tech Stack

| Category | Technology |
|---|---|
| Frontend | React 19 |
| Build Tool | Vite 7 |
| Styling | Tailwind CSS v4 (`@tailwindcss/vite`) |
| Animation | Motion (`motion/react`) |
| Notifications | `react-hot-toast` |
| Linting | ESLint 9 |

## Architecture

This is a client-side SPA (Single Page Application):

- `App.jsx` composes all page sections
- Section components render static content and UI interactions
- Styling is utility-first via Tailwind CSS
- Form submission is sent directly from browser to Web3Forms API
- No custom backend, database, or authentication layer

## Screenshots / Preview

- Hero section preview:  
  ![Hero Preview](./src/assets/hero_img.png)

You can add more screenshots in a `/docs` folder if you want a fuller portfolio presentation.

## Demo / Links

- Live Demo: Not publicly deployed yet (optional)
- Repository: Current repository (`agency-ai`)

## Installation

### Prerequisites

- Node.js `18+` (recommended `20+`)
- npm `9+`

### Steps

```bash
git clone <your-repo-url>
cd agency-ai
npm install
```

## Environment Variables

The current code uses a hardcoded Web3Forms access key.  
For production, move it to an environment variable.

Create a `.env` file in the project root:

```env
VITE_WEB3FORMS_ACCESS_KEY=your_web3forms_access_key
```

Then update `src/components/ContactUs.jsx` to read from:

```js
import.meta.env.VITE_WEB3FORMS_ACCESS_KEY
```

## Running the Project Locally

```bash
npm run dev
```

Then open the local URL shown by Vite (usually `http://localhost:5173`).

## Available Scripts

```bash
npm run dev      # Start development server
npm run build    # Create production build
npm run preview  # Preview production build locally
npm run lint     # Run ESLint
```

## API / External Integrations

This project does not expose internal API routes.

External API used:

- `POST https://api.web3forms.com/submit` for contact form submission

Submitted fields:

- `name`
- `email`
- `message`
- `access_key`

## Usage Guide

- Update content text in section components under `src/components/`
- Replace images/icons in `src/assets/`
- Adjust theme color in `src/index.css` via `--color-primary`
- Edit team and trusted-brand data in `src/assets/assets.js`
- Connect your own Web3Forms access key before production deploy

## Example Workflow

1. Start local dev server with `npm run dev`.
2. Edit `Hero.jsx`, `Services.jsx`, and `OurWork.jsx` for brand content.
3. Replace logos and portfolio images in `src/assets/`.
4. Configure contact form key via `.env`.
5. Run `npm run lint` and `npm run build`.
6. Deploy to Vercel, Netlify, or any static hosting platform.

## Folder Structure

```text
agency-ai/
├─ public/
│  └─ vite.svg
├─ src/
│  ├─ assets/
│  │  ├─ assets.js
│  │  └─ ...images/icons
│  ├─ components/
│  │  ├─ Navbar.jsx
│  │  ├─ Hero.jsx
│  │  ├─ Services.jsx
│  │  ├─ OurWork.jsx
│  │  ├─ Teams.jsx
│  │  ├─ ContactUs.jsx
│  │  ├─ Footer.jsx
│  │  └─ ...shared components
│  ├─ App.jsx
│  ├─ main.jsx
│  └─ index.css
├─ index.html
├─ vite.config.js
├─ eslint.config.js
├─ package.json
└─ README.md
```

## Configuration Notes

- Tailwind is configured through Vite plugin in `vite.config.js`.
- Dark mode uses a class-based strategy via `@custom-variant dark` in `src/index.css`.
- Global styles currently set `cursor: none;` for all elements to support the custom cursor effect.
- Main font is Google Font `Manrope` imported in `src/index.css`.

## Deployment

This app is static-hosting friendly.

### Build

```bash
npm run build
```

### Output

- Production files are generated in `dist/`.

### Common Hosting Options

- Vercel
- Netlify
- Cloudflare Pages
- GitHub Pages (with Vite base-path config if needed)

## Testing

No automated test suite is configured yet.

Current quality checks:

```bash
npm run lint
npm run build
```

Recommended future additions:

- Unit/component tests with Vitest + React Testing Library
- End-to-end tests with Playwright

## Performance, Accessibility, SEO

- Vite build provides fast bundling and optimized static output.
- Motion animations are viewport-triggered for smoother rendering.
- Accessibility note: global `cursor: none` can reduce usability for some users.
- SEO note: currently minimal meta tags in `index.html`; add Open Graph, description, and structured metadata for production.

## Security Notes

- Do not commit real production API keys to source code.
- Move the Web3Forms key to `.env` and rotate compromised keys.
- Client-side form integrations expose request endpoints publicly; use provider-side spam protection features (captcha, domain restrictions).

## Roadmap

- Move form key to environment variable
- Add reusable data layer for services/work/team content
- Add form validation and loading states
- Add tests (Vitest + RTL)
- Add CI workflow for lint and build
- Improve accessibility and keyboard support
- Add multilingual content support

## Known Limitations

- No backend or database
- Contact form key is currently hardcoded in source
- No CMS integration
- No automated tests yet
- Some text/content is static and demo-oriented

## Contributing

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/your-change`.
3. Commit changes with clear messages.
4. Run `npm run lint` and `npm run build`.
5. Open a Pull Request with a short summary and screenshots for UI changes.

## License

No license file is currently included.  
By default, all rights are reserved until a license (for example, MIT) is added.

## Author

- Ormel (based on project footer attribution)
- Customize author details as needed for portfolio/recruiter use

## Acknowledgments

- React team
- Vite team
- Tailwind CSS team
- Motion for React
- Web3Forms for serverless contact form handling

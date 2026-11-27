# AGENCY-AI

AGENCY-AI is a responsive React landing page for a digital agency. It presents agency services, selected work, team members, and a contact form, with light/dark themes and animated UI sections.

## Purpose

The site provides a single-page marketing presence for an agency whose listed services include advertising, content marketing, content writing, and social media. It is designed for prospective clients who want to review agency capabilities and submit an inquiry.

The repository name includes “AI,” but the inspected application is a static agency website rather than an AI application: there are no AI models, AI SDKs, chat interfaces, prompt workflows, or backend services implemented in the source tree.

## Implemented features

- Responsive single-page navigation with section links
- Mobile navigation drawer
- Light and dark themes, persisted in `localStorage`
- System dark-mode preference fallback
- Scroll-triggered and interactive animations
- Custom pointer cursor effect
- Advertising, content marketing, content writing, and social media service cards
- Portfolio/project showcase
- Team member display
- Trusted-company logo section
- Contact form submission through Web3Forms
- Success and error toast notifications
- Footer with newsletter UI and social/contact navigation

## Technology stack

### Frontend

- React 19
- Vite 7
- Tailwind CSS 4
- Motion (Framed Motion-compatible animation package)
- `react-hot-toast`
- Plain JavaScript and CSS

### External service

- [Web3Forms](https://web3forms.com/) for contact-form submission

## Architecture

This is a client-only Vite application. `src/main.jsx` mounts `src/App.jsx`, and `App.jsx` composes the page sections in one root component.

```text
agency-ai/
├── public/
│   └── favicon.ico
├── src/
│   ├── assets/          # Images, logos, icons, and asset exports
│   ├── components/      # Navigation and page sections
│   ├── App.jsx          # Top-level page composition
│   ├── index.css        # Global styles and Tailwind setup
│   └── main.jsx         # React entry point
├── index.html
├── package.json
├── vite.config.js
├── vercel.json          # Vercel SPA rewrite configuration
└── eslint.config.js
```

Key component responsibilities:

- `Navbar` — section navigation and mobile drawer
- `Hero` — introductory heading and hero artwork
- `TrustedBy` — company logos
- `Services` — service descriptions
- `OurWork` — project examples
- `Teams` — team cards
- `ContactUs` — Web3Forms contact submission
- `Footer` — agency summary, navigation, newsletter UI, and links

## Local development

### Prerequisites

- Node.js and npm
- Internet access for npm dependencies and external assets

The repository does not specify a required Node.js version.

### Setup

```bash
git clone https://github.com/sir-hillary/agency-ai.git
cd agency-ai
npm install
npm run dev
```

Vite will print the local development URL in the terminal, typically `http://localhost:5173`.

## Available scripts

| Command | Purpose |
| --- | --- |
| `npm run dev` | Start the Vite development server |
| `npm run build` | Create a production build in `dist/` |
| `npm run preview` | Preview a built application locally |
| `npm run lint` | Run ESLint across the repository |

## Environment variables

No environment variables are referenced in the inspected source code.

The Web3Forms access key is currently embedded directly in `src/components/ContactUs.jsx`. This README does not reproduce that key. For security and maintainability, move it to an environment variable only when the code is intentionally updated to use one.

## Contact and external integrations

The contact form sends a `POST` request to:

```text
https://api.web3forms.com/submit
```

The submitted `FormData` contains the fields `name`, `email`, and `message`, plus the Web3Forms access key. The application displays a success or error toast based on the response. No server-side endpoint, database, or custom mail integration is included in this repository.

The footer newsletter input does not currently submit data or call an API. It should be considered visual UI only.

## Theme behavior

Theme preference uses the `theme` key in browser `localStorage`. On initialization, the application prefers the stored theme and otherwise checks `prefers-color-scheme`.

## Deployment

The repository includes a Vercel rewrite configuration:

```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/" }
  ]
}
```

This configuration serves the root for client routes. The repository metadata identifies the existing site as:

```text
https://agency-ai-gamma-six.vercel.app
```

The deployment URL and Vercel configuration are verified, but deployment credentials and hosting settings outside the repository are not available for inspection.

## Current status and limitations

- The application is an implemented static marketing/agency landing page.
- There is no authentication or user account system.
- There is no database or persistent application data.
- There is no custom backend or API route layer.
- No AI model or external AI service is implemented.
- Team, portfolio, service, and logo data is hard-coded in source and asset files.
- The footer newsletter form has no submission behavior.
- Several social links are rendered as icons rather than verified external profile links.
- The repository does not contain tests or a test script.
- The repository does not include a license file.
- Node.js version requirements, test coverage, and production analytics are unverified.

## Future improvements

The following items are proposals only and are not implemented:

- Add a real newsletter subscription service
- Move the Web3Forms key to a runtime environment variable
- Replace hard-coded marketing content with CMS or structured data
- Add automated component and end-to-end tests
- Add active social profile links
- Add a privacy notice and contact-data handling documentation
- Introduce AI features only if an intended model/provider and backend flow are defined

## Author

**Sir Hillary** — [GitHub](https://github.com/sir-hillary)

- Repository: [https://github.com/sir-hillary/agency-ai](https://github.com/sir-hillary/agency-ai)
- Live deployment: [https://agency-ai-gamma-six.vercel.app](https://agency-ai-gamma-six.vercel.app)

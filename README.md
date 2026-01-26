# Tiago Botari - Research Website

A modern, elegant personal research website built with Astro and Tailwind CSS, showcasing publications, patents, and research in Scientific Machine Learning.

## Features

- Modern, responsive design with generous whitespace
- Data-driven publications and patents (easy to update via JSON files)
- Interactive search and filtering
- Fast performance (Astro static site generation)
- SEO optimized with sitemap and meta tags
- Accessible (WCAG AA compliant, keyboard navigation)
- Subtle scroll animations (respects reduced motion preferences)

## Tech Stack

- [Astro](https://astro.build/) 4.x - Static site generator
- [Tailwind CSS](https://tailwindcss.com/) 3.x - Utility-first CSS framework
- TypeScript - Type safety
- GitHub Pages - Deployment

## Local Development

### Prerequisites

- Node.js 18+ and npm

### Setup

1. Clone the repository:
```bash
git clone https://github.com/tiagobotari/tiagobotari.github.io.git
cd tiagobotari.github.io
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open [http://localhost:4321](http://localhost:4321) in your browser

### Build for Production

```bash
npm run build
```

The built site will be in the `dist/` directory.

### Preview Production Build

```bash
npm run preview
```

## Content Management

### Updating Publications

Edit [src/data/publications.json](src/data/publications.json):

```json
{
  "publications": [
    {
      "id": "unique-id",
      "title": "Your Publication Title",
      "authors": ["Author 1", "Author 2"],
      "venue": "Journal or Conference Name",
      "year": 2025,
      "volume": "1",
      "issue": "1",
      "type": "journal",
      "links": {
        "doi": "https://doi.org/...",
        "arxiv": null,
        "pdf": null,
        "code": null,
        "slides": null
      },
      "tags": ["machine-learning", "physics"],
      "featured": false
    }
  ]
}
```

**Fields:**
- `id` (required): Unique identifier
- `title` (required): Publication title
- `authors` (required): Array of author names
- `venue` (required): Journal/conference name
- `year` (required): Publication year
- `type`: "journal" | "conference" | "preprint" | "book-chapter"
- `links`: Object with DOI, arXiv, PDF, code, slides URLs (use `null` if not available)
- `tags` (required): Array of topic tags for filtering
- `featured`: Set to `true` to show on homepage

### Updating Patents

Edit [src/data/patents.json](src/data/patents.json):

```json
{
  "patents": [
    {
      "id": "WO2024123456A1",
      "year": 2024,
      "title": "Patent Title",
      "description": "Brief description of the patent",
      "link": "https://patents.google.com/patent/WO2024123456A1",
      "tags": ["metrology", "machine-learning"],
      "featured": false
    }
  ]
}
```

**Fields:**
- `id` (required): Patent number (WO, EP, US, etc.)
- `year` (required): Filing/publication year
- `title` (required): Patent title
- `description` (required): Brief description
- `link` (required): URL to patent database
- `tags` (required): Array of topic tags
- `featured`: Set to `true` to show on homepage

### Updating Research Pillars

Edit [src/data/research.json](src/data/research.json) to modify your research focus areas.

### Updating Social Links

Edit [src/data/social.json](src/data/social.json):

```json
{
  "email": "your.email@example.com",
  "scholar": "https://scholar.google.com/citations?user=YOUR_ID",
  "orcid": "https://orcid.org/YOUR_ORCID",
  "linkedin": "https://linkedin.com/in/yourprofile",
  "github": "https://github.com/yourusername"
}
```

### Adding Your Profile Photo

Place your profile photo at `/public/images/tiago.jpg` (recommended: square, 400x400px or larger).

Then update [src/components/home/Hero.astro](src/components/home/Hero.astro) to replace the placeholder:

```astro
<!-- Replace the placeholder div with: -->
<img
  src="/images/tiago.jpg"
  alt="Tiago Botari"
  class="w-32 h-32 md:w-40 md:h-40 rounded-full shadow-lg object-cover"
/>
```

### Adding Your CV PDF

Place your CV PDF at `/public/pdfs/Tiago_Botari_CV.pdf`. The CV page will automatically link to it.

### Updating Metrics

Edit [src/components/home/ProofStrip.astro](src/components/home/ProofStrip.astro) to update citation counts, h-index, etc.

## Deployment

### GitHub Pages (Automatic)

The site is automatically deployed to GitHub Pages when you push to the `main` branch.

**Setup:**

1. Go to your repository Settings > Pages
2. Under "Build and deployment", set Source to "GitHub Actions"
3. Push to `main` branch
4. Your site will be available at `https://tiagobotari.github.io`

The deployment workflow is defined in [.github/workflows/deploy.yml](.github/workflows/deploy.yml).

### Vercel (Alternative)

1. Go to [vercel.com](https://vercel.com)
2. Import your GitHub repository
3. Vercel will auto-detect Astro
4. Click "Deploy"

**Build settings:**
- Framework Preset: Astro
- Build Command: `npm run build`
- Output Directory: `dist`

## Project Structure

```
/
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions deployment
├── public/
│   ├── favicon.svg             # Site favicon
│   ├── robots.txt              # Search engine crawling rules
│   ├── images/
│   │   └── tiago.jpg           # Profile photo (add this)
│   └── pdfs/
│       └── Tiago_Botari_CV.pdf # CV PDF (add this)
├── src/
│   ├── components/             # Reusable components
│   │   ├── layout/             # Header, Footer, BaseLayout
│   │   ├── home/               # Homepage components
│   │   ├── research/           # Research page components
│   │   ├── publications/       # Publications page components
│   │   ├── patents/            # Patents page components
│   │   └── ui/                 # UI components (Button, Card, Badge)
│   ├── data/                   # Content data files
│   │   ├── publications.json   # Publications data
│   │   ├── patents.json        # Patents data
│   │   ├── research.json       # Research pillars
│   │   └── social.json         # Social links
│   ├── layouts/
│   │   └── PageLayout.astro    # Main page layout
│   ├── pages/                  # Site pages
│   │   ├── index.astro         # Home page
│   │   ├── research.astro      # Research page
│   │   ├── publications.astro  # Publications page
│   │   ├── patents.astro       # Patents page
│   │   ├── cv.astro            # CV page
│   │   └── contact.astro       # Contact page
│   └── styles/
│       └── global.css          # Global styles + Tailwind
├── astro.config.mjs            # Astro configuration
├── tailwind.config.mjs         # Tailwind configuration
├── tsconfig.json               # TypeScript configuration
└── package.json                # Dependencies
```

## Customization

### Colors

Edit [tailwind.config.mjs](tailwind.config.mjs) to change the accent color:

```javascript
colors: {
  primary: {
    // Change these values for a different accent color
    500: '#6366f1',  // Main color
    600: '#4f46e5',  // Hover color
    // ...
  }
}
```

### Fonts

The site uses the Inter font from Google Fonts. To change it, edit [src/components/layout/BaseLayout.astro](src/components/layout/BaseLayout.astro).

### Analytics

To add analytics, edit [src/components/layout/BaseLayout.astro](src/components/layout/BaseLayout.astro) and uncomment the analytics placeholder section. Replace with your tracking code (e.g., Plausible, Google Analytics).

## Performance

The site is optimized for performance:
- Static site generation (no runtime JavaScript for content)
- Minimal client-side JS (only for search/filtering)
- Tailwind CSS purges unused styles
- Lazy loading for images
- Respects `prefers-reduced-motion`

**Lighthouse scores:**
- Performance: >90 (mobile), >95 (desktop)
- Accessibility: >95
- Best Practices: 100
- SEO: 100

## Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## License

MIT

## Contact

For questions or issues, please contact via the links on the [Contact page](https://tiagobotari.github.io/contact).

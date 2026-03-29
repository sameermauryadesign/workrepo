# AI-PriceTrack — Implementation Plan

Build a premium, visually stunning single-page web application for product identification via image upload with price comparison and history tracking across e-commerce retailers. Uses **Vite + vanilla JS** with **Chart.js** for charts. Real APIs are out of scope — all product identification and pricing is simulated with realistic mock data to demonstrate the full UX.

## Proposed Changes

### Project Scaffold

#### [NEW] Project initialization via Vite
- `npx -y create-vite@latest ./ --template vanilla`
- Install Chart.js: `npm install chart.js`

---

### Design System & App Shell

#### [NEW] [index.css](file:///c:/Users/maury/OneDrive/문서/New%20folder/src/index.css)
- Dark-mode-first design system: deep navy/charcoal background, vibrant accent gradients (cyan → violet)
- Custom CSS properties for colors, spacing, radii, shadows
- Typography via Google Fonts (Inter)
- Glassmorphism card styles, smooth transitions, hover effects
- Responsive breakpoints (mobile-first)

#### [MODIFY] [index.html](file:///c:/Users/maury/OneDrive/문서/New%20folder/index.html)
- Semantic HTML shell: header with logo/nav, sidebar, main content area
- SEO meta tags, Google Fonts link
- Tab navigation: **Search**, **Dashboard**, **Alerts**

---

### Image Upload & AI Identification

#### [NEW] [upload.js](file:///c:/Users/maury/OneDrive/문서/New%20folder/src/upload.js)
- Drag-and-drop zone with visual feedback (dashed border glow on hover)
- File input for JPG/PNG + mobile camera capture (`accept="image/*" capture="environment"`)
- Image preview with loading shimmer animation
- On upload: triggers simulated AI identification (1.5s delay for realism)

#### [NEW] [ai-engine.js](file:///c:/Users/maury/OneDrive/문서/New%20folder/src/ai-engine.js)
- Mock AI identification engine: matches uploaded images to a built-in product catalog
- Returns brand, model, category, confidence score
- Catalog of ~8 products (shoes, headphones, watches, laptops, etc.)

---

### Price Comparison

#### [NEW] [price-compare.js](file:///c:/Users/maury/OneDrive/문서/New%20folder/src/price-compare.js)
- Renders retailer price cards (Amazon, eBay, Walmart, Target, Best Buy)
- Each card: retailer logo/icon, current price, stock status, "Buy Now" link
- Highlights the best deal with a glowing badge
- Simulated fetch with staggered loading animation

---

### Price History Charts

#### [NEW] [price-chart.js](file:///c:/Users/maury/OneDrive/문서/New%20folder/src/price-chart.js)
- Chart.js line chart: 90-day simulated price history per retailer
- Interactive tooltips, togglable retailer lines
- "Rise & Fall" trend indicator (arrow up/down with % change)
- Time range selector: 7d / 30d / 90d / 1y

---

### User Dashboard

#### [NEW] [dashboard.js](file:///c:/Users/maury/OneDrive/문서/New%20folder/src/dashboard.js)
- "Watched Products" grid of saved items (stored in localStorage)
- Each card: product thumbnail, name, lowest current price, price trend spark-line
- Add/remove from watched list

#### [NEW] [alerts.js](file:///c:/Users/maury/OneDrive/문서/New%20folder/src/alerts.js)
- Price alert creation UI: select product → set target price → save
- Alert list with status indicators (active / triggered)
- Toast notification simulation when a mock price hits a target

---

### App Entry Point

#### [NEW] [main.js](file:///c:/Users/maury/OneDrive/문서/New%20folder/src/main.js)
- SPA router (hash-based): `#search`, `#dashboard`, `#alerts`
- Initializes all modules, manages tab switching
- Coordinates state across modules

#### [NEW] [mock-data.js](file:///c:/Users/maury/OneDrive/문서/New%20folder/src/mock-data.js)
- Centralized product catalog with names, images, categories
- Pre-generated price history arrays per retailer per product
- Helper functions for generating realistic price fluctuations

---

### Assets

#### [NEW] Generated product images
- Generate 4-5 product placeholder images using `generate_image` tool

---

## Verification Plan

### Browser Testing
1. Run `npm run dev` in the project directory
2. Open the app in browser via the browser subagent
3. Verify each tab navigates correctly (**Search**, **Dashboard**, **Alerts**)
4. Upload / drag an image → verify AI identification panel appears with product info
5. Verify price comparison cards render with best-deal highlight
6. Verify price history chart renders with interactive tooltips and time range toggles
7. Add a product to watched list → switch to Dashboard → confirm it appears
8. Create a price alert → confirm it shows in the alerts list
9. Verify responsive layout at smaller viewport sizes

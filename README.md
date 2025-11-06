# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

## Docker (serve built site with nginx)

This project can be built and served using Docker + nginx. The repo includes a multi-stage `Dockerfile` that builds the Vite app and serves the `dist` output with nginx using a provided `nginx.conf` (SPA fallback to `index.html`).

Build the Docker image and run the container (PowerShell / Windows):

```powershell
# build the image (run from project root)
docker build -t ecommerce-product-page:latest .

# run container mapping localhost:8080 -> container:80
docker run --rm -p 8080:80 ecommerce-product-page:latest
```

Open http://localhost:8080 in your browser.

Notes:
- `.dockerignore` is included to keep the build context small (ignores `node_modules`, `.git`, `.github`, and `dist`).
- To deploy to GitHub Pages, you can either:
	- Build locally (`npm run build`) and push the `dist/` contents to the `gh-pages` branch, or
	- Add a GitHub Actions workflow that runs `npm ci && npm run build` and deploys `dist/` to `gh-pages` or to the GitHub Pages site via the `github-pages` action.

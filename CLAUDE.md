# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Morning Seeds is a single-page web application that displays daily wisdom from Ralph Waldo Emerson. The site features QR code generation for mobile access and interactive flip cards showing quotes with explanations.

**Live Site**: https://sphfoeml.manus.space

## Architecture

### Core Structure
- **Single HTML file**: The entire application (`index.html`) is self-contained with embedded CSS and JavaScript
- **Client-side only**: No backend required - runs entirely in the browser
- **Dual interface**: Desktop shows QR code, mobile shows quotes when accessed via `?random=true` parameter

### Key Components
- **QR Code System**: Uses qrcode-generator library to create scannable codes linking to quote interface
- **Flip Card Interface**: CSS 3D transforms create interactive cards with quotes on front, explanations on back
- **Quote Management**: 15 curated Emerson quotes with explanations stored in JavaScript array
- **Responsive Design**: Mobile-first approach with touch support and keyboard navigation

### Data Structure
- Quotes are stored in `emersonQuotes` array within `index.html`
- Standalone `quotes-data.js` exists for reference but is not used by the application
- Each quote object contains `quote` and `explanation` properties

## Development Workflow

### No Build Process
This project has no build system, package.json, or external dependencies (except CDN-loaded QR library). Changes are made directly to `index.html`.

### Testing
- Manual testing across browsers (Chrome, Firefox, Safari)
- QR code scanning testing with mobile devices
- Keyboard navigation testing (F, N, Space, Enter keys)
- Touch interaction testing on mobile devices

### Key Features to Preserve
- **Keyboard Navigation**: F=flip, N=new quote, Space/Enter=interact
- **Animations**: CSS transforms with easing for smooth interactions
- **Accessibility**: ARIA labels, focus states, reduced motion support
- **Performance**: Single file under 50KB, hardware-accelerated animations

## Code Conventions

### CSS
- Glass morphism design with backdrop-filter effects
- CSS custom properties for consistent gradients
- Mobile-first responsive breakpoints
- Smooth animations with cubic-bezier easing

### JavaScript
- Vanilla JS with no framework dependencies
- Event-driven architecture for user interactions
- Progressive enhancement for modern browser features
- Graceful fallbacks for older browsers

### Quote System
- Random selection avoids consecutive duplicates
- Flip card resets to front on new quote generation
- Copy/share functionality with clipboard API fallbacks

## Deployment Notes

The application is deployed as a static HTML file and requires no server-side processing. The QR code generates a link to the same page with `?random=true` parameter to trigger quote display mode.
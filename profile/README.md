# Where Stars Drift ✨

> *An interactive TypeScript space simulation library where celestial mechanics meet artistic expression*

[![npm version](https://img.shields.io/npm/v/@where-stars-drift/core.svg)](https://www.npmjs.com/package/@where-stars-drift/core)
[![License](https://img.shields.io/badge/license-Proprietary-red.svg)](LICENSE)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue.svg)](https://www.typescriptlang.org/)

**Where Stars Drift** is a high-performance canvas-based simulation engine that brings space to life. Watch black holes consume stars, starship fleets navigate in formation, and nebulas drift across the cosmic void - all rendered in real-time with realistic physics.

Born from a simple starfield background, it evolved into a complete 2D space engine inspired by classics like **Homeworld** and **Freelancer**.

---

## 🌌 What Makes It Special

### Real Physics, Beautiful Results
- **Gravitational simulation** with spatial optimization (quadtree)
- **Black holes** that actually consume stars and merge with each other
- **Fleet formations** with tactical AI and collision avoidance
- **60 FPS** with 1000+ entities through aggressive optimization

### Rich Entity System
- **5 black hole types** - Each with unique visual effects (vortex, accretion disk, lensing, warped disk)
- **9 ship categories** - From nimble fighters to massive capital ships
- **Dynamic fleets** - V-formation, defensive sphere, line abreast, and more
- **Clan system** - Color-coded factions with unique behaviors

### Built for Developers
- **TypeScript-first** with full type safety
- **Framework agnostic** - Pure canvas, works everywhere
- **Highly configurable** - Control every aspect of the simulation
- **Performance monitoring** built-in for optimization

---

## 🎮 Live Demo

**Try it:** [Demo](https://migration-script-runner.dev/where-stars-drift) 

**Screenshot:**
*(Coming Soon)*
*A simulation showing a vortex black hole consuming stars while fleets patrol in formation*

---

## 📦 Installation

```bash
npm install @where-stars-drift/core
```

---

## 🚀 Quick Start

### Vanilla JavaScript / TypeScript (Current API - v1.0-1.1)

```typescript
import { WhereStarsDrift } from '@where-stars-drift/core';

const canvas = document.getElementById('canvas') as HTMLCanvasElement;

const simulation = new WhereStarsDrift(canvas, {
  starsCount: 1000,
  interactive: true,
  debug: false,
  showCatalog: false,
  showGrid: true,
  showGithubLink: true
});

simulation.start();

// Get basic stats
const stats = simulation.getStats();
console.log(`FPS: ${stats.fps}, Stars: ${stats.starCount}, Ships: ${stats.starshipCount}`);
```

### React Integration (Current API)

```tsx
'use client';

import { useRef, useEffect } from 'react';
import { WhereStarsDrift } from '@where-stars-drift/core';

export function SpaceBackground() {
  const canvasRef = useRef<HTMLCanvasElement>(null);

  useEffect(() => {
    if (!canvasRef.current) return;

    const simulation = new WhereStarsDrift(canvasRef.current, {
      starsCount: 500,
      interactive: true,
      showGrid: false
    });

    simulation.start();
    return () => simulation.destroy();
  }, []);

  return <canvas ref={canvasRef} className="fixed inset-0 -z-10" />;
}
```

---

## 🎨 Key Features

### Celestial Bodies
```typescript
// Stars with orbital systems
- Regular stars with twinkling
- Pulsars with rotation effects
- Ringed planets
- Multiple orbit lanes with docking points

// Black Holes (5 types)
- Standard: Classic singularity
- Lensing: Gravitational light bending
- Accretion Disk: Rotating matter disk
- Vortex: Swirling particle effects
- Warped Disk: Spacetime distortion

// All with realistic physics:
- Star consumption with supernovas
- Black hole mergers
- Gravitational attraction
- Energy streams between black holes
```

### Starships & Fleets
```typescript
// 9 Ship Categories
- Capital Ships: Dreadnought, Battleship, Carrier
- Cruisers: Heavy, Light, Battlecruiser
- Escorts: Destroyer, Frigate, Corvette
- Support: Monitor, Troop Transport
- Small Craft: Fighter, Bomber
- Exploration: Explorer, Science Frigate, Pathfinder
- Commerce: Hauler, Colony Ship, Shuttle
- Mining: Mining Vessel, Gas Miner, Salvage Ship
- Diplomatic: Courier, Hospital Ship

// Fleet Formations
- V-Formation (classic)
- Line Abreast
- Defensive Sphere
- Column
- Wedge
- And more...

// AI Behaviors
- Patrol between stars
- Dock at orbital stations
- Form/disband fleets dynamically
- Flee from mouse cursor
- Maintain formation spacing
```

### Visual Effects
```typescript
- Nebulas: Drifting cosmic clouds
- Comets: Periodic visitors
- Meteors: Random events
- Supernovas: Explosion effects when stars are consumed
- Energy Streams: Bezier curves between black holes
- Cosmic Dust: Subtle static background layer
- Trails: Ship movement trails
```

### Performance
```typescript
// Optimizations
- Quadtree spatial partitioning
- Frustum culling (off-screen entities skipped)
- Cached array references
- Pre-rendered static layers
- Incremental quadtree updates

// Monitoring
const metrics = simulation.getPerformanceMetrics();
// Returns: fps, avgFps, frameTime, updateTime,
//          renderTime, physicsTime, bottleneck, etc.

// Results
- 60 FPS with 1000 entities
- 45+ FPS with 2000 entities
- Scales to mobile devices
```

---

## ⚙️ Configuration

### Current API (v1.0-1.1)

```typescript
const simulation = new WhereStarsDrift(canvas, {
  // Number of background stars
  starsCount: 1000,              // default: 1000

  // Enable mouse interaction (ships flee from cursor)
  interactive: true,              // default: true

  // Show debug information and FPS counter
  debug: false,                   // default: false

  // Show entity catalog panel (developer tool)
  showCatalog: false,             // default: false

  // Show background sector grid
  showGrid: true,                 // default: true

  // Show "Where Stars Drift" link in corner
  showGithubLink: true            // default: true
});
```

### Runtime Controls (Current API)

```typescript
// Change settings at runtime
simulation.setInteractive(false);           // Disable mouse interaction
simulation.setDebug(true);                  // Show debug overlay
simulation.setShowCatalog(true);            // Show entity catalog
simulation.setShowGrid(false);              // Hide sector grid
simulation.setShowGithubLink(false);        // Hide GitHub link

// Get current statistics
const stats = simulation.getStats();
// Returns: { fps, avgFps, starCount, starshipCount, frameCount }

console.log(`FPS: ${stats.fps.toFixed(0)}`);
console.log(`Stars: ${stats.starCount}`);
console.log(`Starships: ${stats.starshipCount}`);

// Lifecycle methods
simulation.start();     // Start animation loop
simulation.stop();      // Pause animation
simulation.destroy();   // Clean up resources
```

### Coming in v1.2.0

The following features are **planned but not yet implemented**:

```typescript
// 🔮 PLANNED - Not available yet!
const simulation = new WhereStarsDrift(canvas, {
  // Granular entity counts
  entities: {
    starsCount: 1000,
    nebulasCount: 5,
    blackHolesCount: 3,
    starshipsCount: 30,
    fleetsCount: 2,
    clansCount: 3
  },

  // Show/hide specific layers
  visibility: {
    nebulas: true,
    starships: false,
    energyStreams: true,
    cosmicDust: true
  },

  // Black hole type control
  blackHoles: {
    types: ['VORTEX', 'ACCRETION_DISK'],
    distribution: 'equal'
  },

  // Cosmic dust layer
  cosmicDust: {
    enabled: true,
    particleCount: 500,
    twinkleEffect: true
  }
});

// 🔮 PLANNED - Performance metrics
const metrics = simulation.getPerformanceMetrics();
// { fps, frameTime, updateTime, renderTime, physicsTime,
//   bottleneck, performanceScore, ... }

// 🔮 PLANNED - Visibility controls
simulation.setVisibility('nebulas', false);
```

**See:** [v1.2.0 Milestone](./docs/milestones/v1.2.0-milestone.md) for complete roadmap

---

## 📊 Current Status

### ✅ Completed (v1.0-1.1)
- Core simulation engine
- 5 black hole types with unique visuals
- 9 ship categories with 20+ ship classes
- 10+ fleet formations
- Quadtree spatial optimization
- Clan system
- Physics simulation (gravity, collisions)
- Visual effects (nebulas, supernovas, energy streams)
- Debug tools and catalogs
- TypeScript with strict mode
- NPM package published

### 🚧 In Progress (v1.2.0)
- Performance optimizations (frustum culling, caching)
- Enhanced configuration API
- Performance monitoring system
- Class hierarchy refactoring (abstract ships & black holes)
- Cosmic dust layer
- Adaptive quality system

### 🔮 Planned (v1.3.0+)
- Save/load simulation state
- Camera system (pan, zoom, follow)
- Event system for custom behaviors
- Sound effects
- More entity types (wormholes, space stations, asteroids)
- WebGL renderer (optional)

---

## 🎓 Use Cases

### 1. **Website Backgrounds** (main purpose at the moment)
Replace boring static backgrounds with a living universe:
```typescript
const simulation = new WhereStarsDrift(canvas, {
  entities: { starsCount: 500, blackHolesCount: 1 },
  visibility: { starships: false, fleets: false }
});
```

### 2. **Data Visualization**
Represent data as entities:
```typescript
// Each star could represent a data point
// Clusters = black holes
// Connections = energy streams
```

### 3. **Game Prototypes**
Build RTS-style space games:
```typescript
// Already includes:
// - Fleet formations
// - Tactical AI
// - Collision detection
// - Physics simulation
```

### 4. **Educational Tools**
Demonstrate physics concepts:
```typescript
// Gravity simulation
// Orbital mechanics
// N-body problems
// Spatial optimization
```

### 5. **Generative Art**
Create unique cosmic scenes:
```typescript
const simulation = new WhereStarsDrift(canvas, {
  blackHoles: {
    types: ['VORTEX'],
    distribution: { 'VORTEX': 10 }
  },
  entities: { starsCount: 2000 }
});

// Capture frames for artwork
```

---

## 🎯 Philosophy

**Where Stars Drift** is more than a library - it's a love letter to space simulation games.

- **Every black hole tells a story** - Watch them merge, consume stars, and grow stronger
- **Every starship has purpose** - Patrol routes, docking procedures, fleet formations
- **Every star drifts with intention** - Physics-driven, not random

This is a passion project for:
- 🎮 Space game enthusiasts
- 💻 Creative coders
- 🔬 Physics simulation lovers
- 🎨 Generative artists
- 🚀 Anyone who looks up at the night sky and wonders

---

## 🤝 Contributing

This is currently a private project, but contributions are welcome by invitation.

**Interested in contributing?**
- Performance optimizations
- New entity types
- Visual effects
- Physics improvements
- Documentation

Reach out at [@vlavrynovych](https://github.com/vlavrynovych)

---

## 📄 License

**Proprietary License**

Copyright © 2026 Volodymyr Lavrynovych. All Rights Reserved.

This software is proprietary. See [LICENSE](LICENSE) for details.

The NPM package `@where-stars-drift/core` is available for personal and commercial use under specific terms.

---

## 🌠 Acknowledgments

**Inspired by:**
- **Homeworld** series - Formation mechanics and fleet control
- **Freelancer** - Space atmosphere and visual style
- **Elite Dangerous** - Scale and immersion
- The beauty of the cosmos

**Technical Inspiration:**
- Quadtree spatial partitioning
- N-body physics simulation
- Canvas2D rendering optimization

**Special Thanks:**
- To Victoria, the first black hole in this universe 💫
- To everyone who looks up at the stars and dreams

---

## 🔗 Links

- **NPM Package:** [@where-stars-drift/core](https://www.npmjs.com/package/@where-stars-drift/core)
- **Website:** *(Coming Soon)*
- **GitHub Organization:** [@where-stars-drift](https://github.com/where-stars-drift)

---

**Made with ❤️ and TypeScript**

*"In space, no one can hear you compile"* 🚀

---

Photo by <a href="https://unsplash.com/@carloskenobi?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Carlos Kenobi</a> on <a href="https://unsplash.com/photos/a-planet-with-a-star-trail-in-the-background-Knla5kYvsRE?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

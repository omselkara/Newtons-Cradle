# Newton's Cradle - Physics Simulation

![Newton's Cradle](https://img.shields.io/badge/Processing-3.x-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

A realistic physics simulation of Newton's Cradle built with Processing. This interactive application demonstrates the principles of conservation of momentum and energy through an elegant visual representation.

## 📋 Table of Contents
- [About](#about)
- [Physics Concepts](#physics-concepts)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [How to Run](#how-to-run)
- [Controls](#controls)
- [Technical Details](#technical-details)
- [Code Structure](#code-structure)
- [Contributing](#contributing)
- [License](#license)

## 🎯 About

Newton's Cradle is a classic physics demonstration device that illustrates the conservation of momentum and energy. When one ball is lifted and released, it strikes the stationary balls, transmitting a force through them that pushes the last ball upward. This simulation recreates this phenomenon with interactive controls allowing you to manipulate the balls and observe the physics in action.

## 🔬 Physics Concepts

This simulation demonstrates several fundamental physics principles:

### Conservation of Momentum
The total momentum before and after a collision remains constant:
```
m₁v₁ + m₂v₂ = m₁v₁' + m₂v₂'
```

### Conservation of Energy
In elastic collisions, kinetic energy is conserved:
```
v₁ + v₁' = v₂ + v₂'
```

### Collision Formulas
The simulation uses these formulas to calculate post-collision velocities:
```
v₂' = (2m₁v₁ + m₂v₂ - m₁v₂)/(m₁+m₂)
v₁' = v₂ + v₂' - v₁
```

### Gravity
Balls experience gravitational acceleration:
```
g = 1.6/6 (simulation units)
```

## ✨ Features

- **Realistic Physics**: Accurate simulation of elastic collisions and momentum transfer
- **Interactive Controls**: Click and drag balls to set initial conditions
- **Rope Constraints**: Fixed-length rope connections between anchor points and balls
- **Multiple Balls**: Five-ball Newton's Cradle configuration
- **Collision Detection**: Precise ball-to-ball collision handling
- **Pause/Resume**: Toggle simulation with spacebar
- **High Frame Rate**: Smooth animation at 300 FPS
- **Multiple Iterations**: Physics updates run 10 times per frame for accuracy

## 📦 Requirements

- **Processing 3.x or higher**
  - Download from [processing.org](https://processing.org/download/)
- **Java Runtime Environment (JRE)** (comes with Processing)
- **Operating System**: Windows, macOS, or Linux

## 💾 Installation

1. **Install Processing**
   ```bash
   # Download from https://processing.org/download/
   # Follow installation instructions for your operating system
   ```

2. **Clone this repository**
   ```bash
   git clone https://github.com/omselkara/Newtons-Cradle.git
   cd Newtons-Cradle
   ```

3. **Open in Processing**
   - Launch Processing IDE
   - File → Open
   - Navigate to the `Newtons-Cradle` folder
   - Open `Newtons_Cradle.pde`

## 🚀 How to Run

### Method 1: Using Processing IDE
1. Open `Newtons_Cradle.pde` in Processing
2. Click the "Run" button (▶️) or press `Ctrl+R` (Windows/Linux) / `Cmd+R` (macOS)
3. The simulation window will open

### Method 2: Command Line (if Processing is installed)
```bash
processing-java --sketch=/path/to/Newtons-Cradle --run
```

## 🎮 Controls

| Control | Action |
|---------|--------|
| **Mouse Click + Drag** | Grab and move a ball to set initial position |
| **Mouse Release** | Release the ball to start motion |
| **Spacebar** | Pause/Resume simulation |

### How to Use:
1. Click on any ball (the cursor must be within the ball's radius)
2. Drag the ball to a desired position
3. The rope constraint maintains the connection
4. Release to watch the physics in action
5. Press spacebar to pause and observe the system

## 🔧 Technical Details

### Physics Engine
- **Iteration Rate**: 10 physics updates per frame
- **Frame Rate**: 300 FPS for smooth simulation
- **Collision System**: Elastic collision model with momentum conservation
- **Constraint Solver**: Distance-based rope constraint enforcement

### Ball Properties
| Property | Value | Description |
|----------|-------|-------------|
| Mass (m) | 1 | Mass of each cradle ball |
| Size | 25 | Radius in pixels |
| Collision | Enabled | Can collide with other balls |
| Gravity | 0.267 | Acceleration due to gravity |

### Anchor Points
- **Mass**: 1 (lightweight)
- **Size**: 1 (nearly invisible)
- **Locked**: True (fixed position)
- **Collision**: False (don't interact)

### Coordinate System
- **Canvas Size**: 600x600 pixels
- **Origin**: Top-left corner (0,0)
- **Y-axis**: Increases downward (standard Processing)

## 📁 Code Structure

The project consists of four main Processing files:

### `Newtons_Cradle.pde` (Main File)
- Main setup and draw loop
- User input handling (mouse and keyboard)
- Global simulation state management

### `Ball.pde`
- Ball class implementation
- Physics calculations (velocity, acceleration, collision)
- Collision detection and response
- Movement and rendering

### `Rope.pde`
- Rope constraint system
- Distance constraint enforcement
- Connects balls to anchor points
- Maintains fixed-length connections

### `Wall.pde`
- Wall/boundary class
- Line segment collision detection
- Normal vector calculations
- Bounce mechanics (currently unused in main simulation)

### Key Classes and Their Responsibilities

```
Ball
├── Properties: position, velocity, mass, size
├── Methods: move(), check(), bounce(), show()
└── Physics: Handles gravity and elastic collisions

Rope
├── Properties: two Ball references, fixed length
├── Methods: move(), show()
└── Constraint: Maintains distance between balls

Wall
├── Properties: two endpoints, angle, normal vectors
├── Methods: coliding(), show()
└── Collision: Line-to-circle collision detection
```

## 🎨 Customization

You can modify the simulation by changing these parameters in `setup()`:

```processing
// Change number of balls
balls.add(new Ball(x, y, velx, vely, mass, size, colide));

// Adjust gravity
float g = 1.6/6;  // In Ball.pde

// Modify frame rate
frameRate(300);  // Higher = smoother, but more CPU intensive

// Change physics iterations
int iter = 10;  // More = more accurate but slower
```

## 🧪 Experiments to Try

1. **Different Initial Conditions**
   - Lift multiple balls simultaneously
   - Give balls different starting velocities
   - Observe momentum transfer patterns

2. **Parameter Modifications**
   - Change ball masses to create asymmetric collisions
   - Adjust gravity to simulate different environments
   - Modify iteration count to see stability effects

3. **Configuration Changes**
   - Add more balls to the cradle
   - Change rope lengths
   - Experiment with different ball arrangements

## 🐛 Known Limitations

- Walls are implemented but not used in the current simulation
- Energy loss may occur over time due to numerical precision
- No damping or friction modeling
- Fixed canvas size (not responsive)

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes**
4. **Commit with descriptive messages**
   ```bash
   git commit -m "Add: description of your changes"
   ```
5. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```
6. **Create a Pull Request**

### Ideas for Contributions
- Add sound effects for collisions
- Implement energy visualization (graphs)
- Add different ball materials with varying elasticity
- Create multiple cradle configurations
- Add export/recording functionality
- Implement walls in the simulation
- Add touch controls for mobile Processing

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👤 Author

**omselkara**
- GitHub: [@omselkara](https://github.com/omselkara)

## 🙏 Acknowledgments

- Inspired by the classic Newton's Cradle physics demonstration
- Built with [Processing](https://processing.org/), an open-source creative coding platform
- Physics formulas based on classical mechanics principles

## 📚 Resources

- [Processing Documentation](https://processing.org/reference/)
- [Newton's Cradle - Wikipedia](https://en.wikipedia.org/wiki/Newton%27s_cradle)
- [Conservation of Momentum](https://en.wikipedia.org/wiki/Momentum#Conservation_of_momentum)
- [Elastic Collision](https://en.wikipedia.org/wiki/Elastic_collision)

---

**Enjoy exploring the physics of Newton's Cradle! 🎯**

For questions, issues, or suggestions, please open an issue on GitHub.

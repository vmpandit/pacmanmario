Pac-Mario: Neon Edition 🕹️🍄
A 32-bit hybrid game engine built entirely in a single HTML file using vanilla JavaScript.

Play it now: Just download pacmario_final.html and open it in any browser!

📖 About the Project
Pac-Mario: Neon Edition is a genre-bending web game that fuses the top-down maze mechanics of Pac-Man with the side-scrolling physics of Super Mario Bros. It features a custom-built game engine that seamlessly switches between two distinct gameplay modes.

This project serves as a technical demonstration of AI-Assisted Development, utilizing Google Gemini Pro to architect, debug, and optimize a complex JavaScript application without external libraries or assets.

🎮 Gameplay Features
Dual-Mode Engine: Transitions instantly between Top-Down Maze (RPG style) and Side-Scrolling Platformer (Physics style).

Procedural Level Generation: Maps are generated via code, ensuring endless variations of mazes and platform runs.

Runtime Asset Synthesis: No images or MP3s are loaded. All sprites (32-bit pixel art) and audio effects are generated programmatically by the browser canvas and Web Audio API at runtime.

Mobile & Desktop Support: Responsive canvas scaling with integrated touch controls for mobile devices.

🛠️ Technical Architecture
This game was built using advanced vanilla JavaScript techniques, prompted and refined through Google Gemini Pro.

1. The "Single-File" Constraint
The entire game (Logic, Rendering, Assets, Audio, Styles) is contained within a single HTML file (< 25kb). This required strict code organization and zero external dependencies.

2. Runtime Asset Generation
Instead of loading .png sprites, the engine uses an Offscreen Canvas Factory:

javascript
// Example: Creating a sprite in memory via code
function genSprite(key, w, h, fn) {
    const c = document.createElement('canvas');
    c.width = w; c.height = h;
    const ctx = c.getContext('2d');
    fn(ctx, w, h); // Draw commands (fillRect, arc, bezierCurve)
    GFX[key] = c;  // Cache for rendering loop
}
This technique, suggested by Gemini Pro, eliminates network latency and allows for dynamic asset coloring.

3. State-Driven Game Loop
The main loop (requestAnimationFrame) is decoupled from the logic update rate to ensure smooth 60fps rendering on high-refresh displays while maintaining deterministic physics. The GAME state object acts as a central store, allowing the engine to hot-swap between MAZE and PLATFORM logic blocks dynamically.

4. Procedural Audio Synthesis
The Web Audio API is used to create sound effects on the fly. Gemini Pro provided the oscillator configurations to mimic retro 8-bit sounds (Square waves for coins, Triangle waves for jumps, Noise buffers for explosions).

🤖 Development with Google Gemini Pro
This project showcases the capabilities of Large Language Models (LLMs) in full-stack game development. Gemini Pro was utilized for:

System Architecture: Designing the flowchart for the hybrid engine (Input -> State -> Physics -> Render).

Algorithm Implementation: Writing the AABB collision detection and "Coyote Time" jump physics for the platformer mode.

Creative Asset Design: Generating the canvas drawing commands to create recognizable sprites (Mario, Ghosts, Pipes) without visual reference files.

Debugging: solving complex race conditions in the AudioContext initialization and fixing "tunneling" bugs in the collision physics.

🚀 How to Run Locally
Clone the repository:

bash
git clone https://github.com/yourusername/pac-mario-neon.git
Navigate to the directory:

bash
cd pac-mario-neon
Open index.html (or pacmario_final.html) in your preferred web browser.

No npm install or build server required!

🕹️ Controls
Action	Desktop (Keyboard)	Mobile (Touch)
Move	Arrow Keys / WASD	Virtual D-Pad
Jump	Spacebar / Enter	Red 'A' Button
Start	Click "Initialize"	Tap "Initialize"
📄 License
Distributed under the MIT License. See LICENSE for more information.

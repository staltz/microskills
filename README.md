# Microskills

Modular prompts I use every day. Compatible with [skills.sh](https://skills.sh) and any agent that reads `SKILL.md`.

Most skills are too verbose. They pollute context with instructions the model already understands. Frontier models are good at paying attention to what you say, so it's sufficient to use few words. Plus, you can read these microskills yourself and know what they're doing.

## Install

```bash
npx skills add staltz/microskills
```

Pick the skills you want and which agents to install them on. The installer writes them into your project as ordinary files you can edit.

## Skills

### ✨ [peep](skills/peep/SKILL.md)

Plain English Expository Prose. Makes the agent speak like a normal person, with a hard word cap. Pass a max: 25 or 100 are common choices.

Examples:

Prompt: `How do airplanes fly? /peep 25` (GPT-5.6 Sol High)

> Airplanes fly because wings force air downward. That action produces an equal upward reaction, lifting the plane while engines push it forward.

Prompt: `How do airplanes fly? /peep 100` (GPT-5.6 Sol High)

> Airplanes fly because their wings and engines work together against gravity. As the plane moves forward, air splits around each wing. The wing's curved top and angled bottom push air downward. By Newton's third law, that downward shove produces an equal upward force called lift. Engines provide thrust, which keeps air flowing over the wings fast enough for lift to exceed weight. The tail and movable flaps on the wings change how air flows, so the pilot can climb, turn, and stay balanced. When lift, thrust, weight, and drag are in the right balance, the airplane stays in the air.

As a counter example, the answer ChatGPT with Sol gave me for vanilla `How do airplanes fly?` had 340 words and a diagram. A bit too verbose in my opinion. You can choose how verbose you want the responses to be.

### ✨ [debrief](skills/debrief/SKILL.md)

Good for listing the decisions the agent made after an ambitious multi-million token session. Useful when reviewing a large agent PR: see the judgment calls first, then dive into the code.

I often find this easier than spending time planning, since during PR review I can change decisions anyway, or simply discard the PR and start over wiser.

Example: I had a Claude Fable 5 session building a 3D world in Three.js, and this is what the `/debrief` prompt got as a response:

> **Project setup**
> - Put the project at the repo root rather than a subfolder
> - Chose Vite + three (^0.180) as the stack, plain JS, no TypeScript
> - Wrote a `.claude/launch.json` entry on port 5194 to drive the preview
> - Added a README nobody asked for
>
> **World plan**
> - Named it Olympia Station in Arcadia Planitia, sol 3117, late afternoon
> - Seven regions: city plateau, landing field, solar flats, crater field, dune sea, north ridge, plain
> - Left the dune sea and ridge deliberately empty
> - Invented named landmarks: domes Concordia/Bradbury/Kim Stanley/Weir, the *MSV Beagle*, the *Erebus* water rig, the *Pathfinder 9* wreck with a memorial flag
> - Chose greenhouses with magenta grow-lights as the city's color accent
> - Picked 640 m world size, 256-segment grid, seed 31170
>
> **Terrain design**
> - Region blending via domain-warped soft weights, with settlement pads resisting the warp
> - Craters suppressed under city/landing pads so floors stay flat
>
> ... (and 320 more words)

### ✨ [where](skills/where/SKILL.md)

Points to where a feature or concept is implemented. A shortcut for Ctrl+F or grep. Pairs really well with Cursor's browser "picker" to point at some element, then `<div /> /where` to find its implementation.

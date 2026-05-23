# my-virtual-pet

An AR virtual pet Android game built in Unity (C#) with Google ARCore, inspired by My Talking Tom. Place your pet in the real world via augmented reality, interact with it through touch, level it up, manage its inventory, and play Tic-Tac-Toe against it.

---

## Features

### Augmented Reality
- Pet is placed and rendered in the real world using **Google ARCore**
- Move, rotate, and resize the pet with touch gestures:
  - **Move** — single finger drag (translates on X/Z world axes)
  - **Rotate** — single finger drag in rotate mode (rotates on Y axis)
  - **Rescale** — two-finger pinch/spread (scales uniformly, clamped at minimum size)
- Switch between 3 characters: **Mousey**, **Doozy**, **Demon**

### Touch Interactions & Animations
- **Stroke** (finger drag on pet) → laughing animation
- **Tap** (finger tap on pet) → hit animation with counter; 3+ rapid hits triggers a special reaction
- Hit counter auto-resets every 4 seconds
- **Wave** animation — unlocked at level 10+
- **Angry** animation — unlocked at level 20+

### Experience & Leveling
- XP-based level system up to 100+
- Non-linear XP scaling per level tier:
  - Levels 1–10: +20 XP per level
  - Levels 10–20: +30, 20–30: +50, 30–40: +80, 40–50: +130 ... up to +1140 per level near 100
- XP gained from using inventory items and winning Tic-Tac-Toe

### Inventory System
- Singleton inventory with configurable slot capacity
- Items defined as **ScriptableObjects** (icon + XP value)
- Using an item grants its XP and removes it from inventory
- **Daily reward** — one random item added every 24 hours via coroutine scheduler

### Save System
- Game state (level, XP, active character) serialized to binary file via `BinaryFormatter`
- Persists across sessions using `Application.persistentDataPath`

### Mini-game: Tic-Tac-Toe
- Player (X) vs computer (O)
- Computer plays randomly on a 0.5s delay
- Win detection for all rows, columns, and diagonals
- Draw detection after 9 moves
- Winning a game grants +1 XP

---

## Tech Stack

| Layer | Technology |
|---|---|
| Engine | Unity |
| Language | C# |
| AR | Google ARCore |
| Platform | Android |

---

## Running the project

Open in Unity with ARCore SDK configured, build to an ARCore-compatible Android device.

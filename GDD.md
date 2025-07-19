# TowerBreakout GDD


## Game Overview

A hybrid game blending mechanics from **Tower Defense** and **Breakout**. Players build and upgrade towers that launch bouncing balls. These balls reflect off walls, enemies, and objects. The player controls a **paddle** to keep balls in play, manipulate their movement, and optimize enemy destruction.

The core gameplay loop focuses on **crafting towers**, **customizing ball effects**, and **environmental strategy**.


## Core Gameplay Pillars

- **Ball-based Defense Mechanics** (physics-driven projectile bouncing)
- **Tower Crafting & Upgrading**
- **Ball Customization via Stackable Effects**
- **Active Paddle Interaction**
- **Dynamic Level Objectives (Economy, Waves, Score)**
- **Reactive Environment (boosts, traps, modifiers)**


## Towers

- Towers shoot balls.
- **Balls** are independent units with their own properties and upgrades.
- Towers and balls are upgraded separately.
- Towers are **crafted** using resources.
- Towers are placeble at the bottom of the screen above a paddle
- Tower can be rotated, on a cooldown or a animation limitaton, so that the player can refocus enemies
- Towers can be build whenever and also destoyed, but with less resouces returning if not in building phase. 
- Towers per level is limited by space
- Tower can be moved between waves

### Upgrades

- Multi-shot
- Charge-up attack


## Balls


### Core Properties

- **Mass** – heavier = slower launch
- **HP**
    - reduced by bouncing
    - increased by paddle bounce
    - ball is destroyed when reaches 0
- **Effects** – stackable, combinable


### Triggers

- On launch
- On hit
	- Wall
	- Enemy
  	- Object
 	- Another ball
- On destruction
- On timer


### Effects

You can chain effects on each other based on what type of effects they are

Types of effects:

- Target dependent
	- effect that must have a target
	- simple hit
	- freeze
	- etc.
-	Effects that return a target
	-	shockwave
	-	lighting strikes 
	-	etc.
-	Conditional effects
	-	if speed of ball is higher than then
	-	if ball bounced enough times


Effects:

- Basic - Bounces off surfaces, deals damage on hit
- AOE - Area damage on hit
- Spawner - Spawns smaller balls on hit or on timer
- Speed-Based Damage - Higher velocity = more damage
- Wall Bounce Scaling - Each bounce increases damage
- Ghost - Passes through objects
- Conditional - Activates damage under conditions (e.g. after N bounces)
---
- Basic Hit
	- Input: Target
	- Output: Void
	- Mechanic: damages object
	
- AOE
- 



### Bounce Types

- **Normal** – standard reflection
- **Reverse** – reflects backward
- **Sniper** – locks on closest enemy
- **Cannonball** – goes straight after killing a target


## Tower/Ball hierarchy example

- Tower
	- Launch power - int(60)
	- Fire-rate - float(1.5)
	- Upgrades
		- Brr
	- Ball
		- Mass - int(10)
		- Hp - int(10)
		- Bounce type(Normal, Reverse, etc.)
		- Upgrades
			- Collision balls - collides with other balls
		- Triggers
			- Enemy-hit
				- Damage(10)
				- Shock wave


## Paddle

- Can deflect balls - healing them so that you can bounce balls back to back
- Damages enemies on contact, reducing it's lenght(HP)


### Variants

- Normal - Standard reflection
- Fan Paddle - Blows balls in a direction
- Magnetic - Attracts or repels balls
- Stuck Paddle - Holds and releases balls
- Bouncy Paddle - Stronger knockback


### Power-Ups / Power-Downs

Power-Ups and Power-Downs are pickable effect that are rendomly spawned into the level on enemy death and fall down pass the paddle. If the paddle catches them the effect applies.

**Power-Ups:**

- Paddle stretch (wider)
- Stronger bounce
- Ball duplication
- Paddle speed boost
- Damage all enemies (shock wave)
- Paddle shoots projectiles

**Power-Downs:**

- Narrower paddle
- Weak rebounds
- Frozen paddle (temporarily disabled)


## Structures

Structures are a placeable entities for example:

- Speed boost for balls
- Reflector - launches balls in specific direction
- Healer - heels balls
- Damage booster 
- Cloner - clones balls that passes through


## Enemies

Enemies move on a predefined path wich must end behind a border. When they completely cross said border, the player loses some income.

If we want a satisfying feeling hitting enemies there must be a big visible chnage. Either make enemies die on one hit. That is the most satisfying version. But you cannot scale it. Or do a multiple hits with a big visual change like color change. Example Idle Breakout.


### Special Types

- Ball-Eater - Destroys balls on contact
- Freezer - Temporarily freezes nearby balls 
- Damage - Resistant - Immune to certain ball effects
- Reflector - Reflects balls back on contact
- Freeze - Freezes any balls that hit it for a short duration
- Shield - Has a special shield, vulnerable only to specific ball effects (e.g. fire)
- Spawner - On damage or death, releases mini-trucks that continue toward the goal


## Environment & Map Interactions

- Grass / Asphalt - Slows down balls
- Boost Pads - Accelerate balls
- Breakable Traps - Spikes, crushers
- Death Zones - Sand trap, black hole


## Level Objectives & Economy


### Primary Goal

- Earn a specific amount of **money** before the level ends.
- If the target is missed → **bankruptcy**, retry level.
- Money is earned **passively** through **distribution of a drink product** (`$ / s`).


### Threat Mechanic

- Enemy **corporation** brings **competing product** via **space trucks**.
- If trucks reach the **border station**, player’s `$ / s` drops.
- The income **recovers slowly** over time.
- More trucks = deeper loss = longer recovery.


### Player Counterplay

- Destroyed enemy trucks drop **resources** (e.g. 4 material types).
- Use them to launch **advertising campaigns**:

  - Restore `$ / s` faster
  - Temporarily boost income
  - Apply global effects (e.g. slow enemies, buff towers)


### Level Structure

- Levels are wave-based (classic TD progression).
- Trucks passing isn’t instant-fail → **only affects income**.
- Level ends when wave cycle is complete; check if **goal earned**.


## Visual Theme / Setting

- space 
- on water, boats - enemies


## Research

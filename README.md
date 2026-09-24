# Borderline Dominion

A full-screen territory strategy prototype covering Europe, western/central Russia, the Middle East, and North Africa.

## Run it

From this folder, start a local server:

```sh
python3 -m http.server 4173
```

Then open [http://localhost:4173](http://localhost:4173).

The first load needs an internet connection to download the geographic border data and the two small map-rendering libraries.

## Current rules

- Choose one or two human players and three to twenty total players.
- Every territory is assigned and colored before the first turn begins.
- Each player starts with a connected block of neighboring territories rather than scattered countries.
- Zoom with the mouse wheel or the `+` and `−` controls, drag to pan, and use the home button to reset the map.
- Country and Russian-region names are enabled by default. Collision handling shows only labels that fit, and progressively reveals smaller places as you zoom closer; **Place names** can still hide them.
- Human and AI realms receive logical names based on their starting location. Entering a custom setup name overrides the automatic name.
- Player names are enabled by default. Each label searches outward from the realm's true middle for the nearest position where the complete banner fits, can wrap onto two lines, rotates south-to-north for tall realms, and moves after conquests. **Player names** can hide them.
- Label placement is cached between turns, so the map does not rebuild unchanged labels during ordinary actions.
- If a realm has disconnected holdings, its name is centered only on its largest continuous landmass; smaller separated holdings are ignored for label placement.
- Realm labels automatically shrink or hide to prevent overlap. The **Name size** slider provides manual control from 4–14.
- Every edge and corner of a realm-name banner must fit inside the player's largest landmass; otherwise it shrinks or waits until the map is zoomed closer.
- `Fast AI` removes the visible delay from AI turns without automating or skipping any human turn.
- Attack modes are optional: **Normal** allows 1 attack per territory, **Moderate** allows up to 3 total attacks for the realm, and **Hard** lets the realm use every available territory once. Every attacking territory fades after attacking, only neighboring territories can be targeted, and a newly captured territory waits until the next turn before attacking.
- A realm can maintain at most 2 active alliances. The same alliance offer cannot be sent repeatedly in one turn. In Hard mode, after every complete round (all active realms have acted), the single largest realm gets one random territory rising in rebellion; rebels do not attack, and the territory must be conquered to recover it.
- A realm that attacks another realm during a round cannot request or accept diplomacy with that realm during the same round. It may try again in the following round after proving it did not attack.
- **Save** or **Load** stores campaigns in this browser. **Cmd+S** (or **Ctrl+S**) opens the save-name prompt.
- **Strengths** is an optional rule in every attack mode. When enabled, successful attackers gain up to +3 attack strength, defenders that hold gain up to +3 defense strength, and captured territories reset their bonuses.
- During a human turn, the Diplomacy panel can target any active realm with a 3-turn alliance or 1-turn ceasefire. Active agreements block attacks in both directions; AI realms may also form short agreements. Wars still require a border.
- AI realms can now send incoming alliance or ceasefire offers. A popup lets the human commander accept or reject each offer; unanswered offers expire automatically.
- **Music: Off/On** toggles an original campaign-style ambient soundtrack from either the setup panel or map controls. It is off by default and uses no external audio file.
- Russia is divided into 64 real administrative regions, so it takes many victories to conquer.
- Select one of your countries, then a highlighted neighboring enemy to attack.
- Each owned country may attack once during its commander's turn.
- The attacker rolls against the defender. A higher attack roll conquers the territory; ties favor the defender.
- The first commander to own the whole region wins.
- A player is eliminated immediately after losing their final territory. Eliminated players are skipped, and the last surviving realm wins.

Marked sea routes connect selected islands and close coasts, including Britain–France, Spain–Morocco, Italy–Tunisia, and Cyprus–Turkey/Syria.

Russian regional boundaries are based on OpenStreetMap-derived administrative data from the public `rnekrasov-msk/geojson` dataset. Crimea and Sevastopol are excluded from the Russian subdivision layer to avoid overlapping Ukraine on the game board.

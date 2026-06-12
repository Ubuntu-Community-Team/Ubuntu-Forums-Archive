---
title: "Package installation"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by rayhipkiss on 2009-09-20
I have installed several packages using Synaptic package manager, but some packages do not show up in any of the menus, e.g. some games I installed don't show in the games menu. Any help is appreciated.

---

### Post by Partyboi2 on 2009-09-20
Some packages are started from the terminal, if you install a package that has a gui check System>Pref>Main Menu that it is listed and has a tick next to it.

---

### Post by rayhipkiss on 2009-09-20
Thanks for the info. However, one of the programs not showing up is Ace of Penguins. I can't find it anywhere.

Thanks.

Ray

---

### Post by Partyboi2 on 2009-09-20
I just installed it to have a look, to run the games you can open a terminal and type one of these depending on which game you want to play
```
/usr/games/ace_golf
/usr/games/ace_mastermind
/usr/games/ace_merlin
/usr/games/ace_pegged
/usr/games/ace_solitaire
/usr/games/ace_taipedit
/usr/games/ace_taipei
/usr/games/ace_thornq
/usr/games/ace_canfield
/usr/games/ace_freecell
/usr/games/ace_minesweeper
```If you are wanting them to appear in the Applications Menu under games you will need to add the item to Main menu for each game.
System>Pref>Main Menu
Click on the games menu on the left,
Click on 'New Menu' (right window) and add for the name something like 'Ace of Penguins' 
Then on the left window select 'Ace of Penguins' and choose 'New Item' and add the game you want eg.
Type: Application
Name: Ace Merlin
Command: /usr/games/ace_merlin
Comment: Blank or add something.
Click on the spring icon and change icon to what ever you like.

---

### Post by rayhipkiss on 2009-09-21
Excellent:)   That done the trick.


 Many thanks


Ray

---


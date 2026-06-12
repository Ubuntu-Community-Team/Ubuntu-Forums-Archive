---
title: "HELP! New Ubuntu 8.10 user..."
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by kedds08 on 2008-12-03
I am new to Linux/Ubuntu, and I am trying to figure this all out on my own, but I am having quite a bit of trouble since I am used to using Windows. I am currently running Ubuntu 8.10, and I have tried to install a flash player, but it isn't working correctly. I keep getting an error: WRONG ARCHITECTURE "i386"... I have been researching, and I have found a few message boards trying to explain, but I am feeling really stupid right now cause I don't know what they are talking about. Where do I type commands? What version of the flash player do I need? Any other tips that you can throw at me are greatly appreciated!!

Krystal

---

### Post by razy60 on 2008-12-03
If you go to System-administration- synaptic package manager then in the search bar type flash player it should give you the option of loading what you need.
  The other option is to go to say youtube or similar, where it will ask you to download or update, then give you the automated links to do so.

---

### Post by oldos2er on 2008-12-03
Type commands into a terminal. Look under the menus Applications, Accessories, Terminal. Or, another way of bringing up a terminal is to hit Alt-F2, then type in "gnome-terminal" without the quote marks.

 Here's a command to practice on. Copy and paste this into a terminal, and show us the output if you would please:

 sudo aptitude update && sudo aptitude safe-upgrade

---


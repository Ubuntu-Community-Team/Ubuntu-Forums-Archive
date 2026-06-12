---
title: "[SOLVED] Problem in KPovModeler"
date: 2008-08-14
forum: General Help
---

### Post by 5l4y3r on 2008-08-14
Hi, I'm having some trouble here using KPovModeler. I don't know if what's happening it's being caused by my graphics card (Radeon 9600 Pro) or by the application itself. There is supposed to have four views in the program, each one showing an angle of the 3D object that I'm building, but instead of these views I have 4 black screens that shows nothing. If I try to render the file that's OK, but without the the views I can't model nothing on the program. 
I'm sending a print of the screen with the 4 black screens.
I have Ubuntu 8.04 and the latest Catalyst drivers for the Radeon. 
Thanks for any help.

---

### Post by 5l4y3r on 2008-08-26
I've found what was wrong: I needed to install xserver-xgl in order to make it work properly. After installing it (by Synaptic) and restarting Ubuntu, the views showed properly.

---


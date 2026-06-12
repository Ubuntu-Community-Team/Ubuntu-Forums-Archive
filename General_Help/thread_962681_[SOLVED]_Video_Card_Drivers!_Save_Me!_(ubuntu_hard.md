---
title: "[SOLVED] Video Card Drivers! Save Me! (ubuntu hardy)"
date: 2008-10-29
forum: General Help
---

### Post by Iron Coney on 2008-10-29
So I need to figure out how to find out if my drivers are updated or not for my video card, and I don't know how to determine that. 

Basically Ive been having video issues today out of nowhere when trying to play WoW in particular (through wine), when it was working fine yesterday...but Im having a heck of a time reinstalling the video drivers. When I try to go to:
System>Administration>Hardware Drivers, and simply check the box to enable the NVIDIA drivers (currently says 'not in use'), the computer crashes on restart and makes a mess, goes into 'low graphics mode' and all that. 

I've also done sudo apt-get install nvidia-glx in the terminal, but I dont know if that worked or not. I've also done some editing on xorg.conf, to no avail. 

So far, the best results I can get are from simply reseting the xorg.conf altogether, which I have done by entering sudo dpkg-reconfigure -phigh xserver-xorg into the terminal, this at least gives me the resolution and functionality that I desire, but Warcraft still gives me the infamous #132 error immediately on startup, so I figure I must in installing the drivers incompletely. 

Suggestions?

---

### Post by Titan8990 on 2008-10-29
Try envyng, it automates the driver download/installation process:


sudo apt-get install envyng-gtk


Then it will be located in Applications -> System Tools

---

### Post by Iron Coney on 2008-10-29
Bro....you...rock...Ive been pullin my hair out all morning over this thing, it appears to be working perfectly, Im definitely going to have to remember that program. Awesome, big thanks. Im gonna have to send you an Xmas card =D.

---

### Post by Titan8990 on 2008-10-29
Glad I could help :).

Don't forget to mark your thread as solved.

---


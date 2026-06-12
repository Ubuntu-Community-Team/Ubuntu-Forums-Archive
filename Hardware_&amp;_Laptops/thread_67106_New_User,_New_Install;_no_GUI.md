---
title: "New User, New Install; no GUI"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by charley on 2005-09-19
I had Ubuntu up and running, and liked it.  But I needed a new video card.  Once I put in the card the existing system wouldn't start the GUI (x-system ?) so I reinstalled hoping that would install the correct drivers.  No Luck.  I get to the login screen, but can't see it.

System:
AMD 2400 chip
ASUS board
GeForce 6600GT video card
Turtle Beach sound card
1 Gig memory
40 Gig ATA Hard drive

With the #2 choice from GRUB I can get to a prompt, but then I have no idea what commands to issue, directories to look in.  I'm afraid I need a fairly simple, streight forward list of things to do to fix the problem.  I don't need the latest greatest drivers on the Ubuntu side, I just need to see the interface.

Thanks in advance,
Charley

---

### Post by tseliot on 2005-09-19
Boot using the 2nd choice as you did before (Recovery mode).

type:
nano /etc/X11/xorg.conf

and Then find the section Device and make sure the word I put in red is &#8220;vesa&#8221;:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR=Red]nvidia[/COLOR]"
BusID "PCI:1:0:0"

CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

Then type "startx" or restart your computer, tell me if it works

---

### Post by charley on 2005-09-19
It worked !
And great instructions.
Thank you very much.

Charley

---


---
title: "Installing drivers from command line?"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by munkifisht on 2009-10-25
I ran into some problems with the graphics drivers on my machine. I updated them but there was a power cut as they updated and the computer shut off. I can now only boot to the command line. Can someone explain to me how to reinstall/repair the graphics drivers from the command line?

---

### Post by munkifisht on 2009-10-25
Solved it, did a mix of this:
[http://ubuntuforums.org/showthread.php?t=1252015](http://ubuntuforums.org/showthread.php?t=1252015)

Firstly, boot to the command line with networking

Run
> sudo apt-get autoremove xserver-xorg
Then
> sudo apt-get install xserver-xorg
Reboot, you get safe graphics mode, select restore generic drivers and reboot and problem solved

---


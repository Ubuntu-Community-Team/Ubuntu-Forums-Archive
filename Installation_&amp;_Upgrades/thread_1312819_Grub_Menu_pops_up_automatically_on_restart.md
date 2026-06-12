---
title: "Grub Menu pops up automatically on restart"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by christoforever on 2009-11-03
So I've done a fresh Kubuntu 9.10 install and the grub menu pops up every time I turn on my computer ... which I then have to hit enter to boot the selected OS. Is there someway I can turn this off?

---

### Post by NoaHall on 2009-11-03
sudo apt-get install startupmanager
Have a play with that.

---

### Post by drs305 on 2009-11-03
For StartUp-Manager instructions/information, check out this thread:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")
StartUp-Manager can tweak settings without going "under the hood". Set the timeout to 0 and you won't see the menu at boot up.


You can also edit the file that controls the setting. There are several links in my signature line that tell you how to do so. For a complete introduction to Grub 2, click on the GRUB2 or "G2 Basics" link.

For an express post about how to make the basic changes often made to the GRUB 2 menu, check out the "G2 - Tasks" link.

---

### Post by christoforever on 2009-12-01
This is a bit late but I've figured out what the problem was ... or maybe it's a bug. When my computer first starts, if I hit escape, that seems to toggle something in grub which makes it pop-up every time I turn my computer on. If I hit escape again, it toggles off. Bug or a feature? I'll be damned if I know :)

---


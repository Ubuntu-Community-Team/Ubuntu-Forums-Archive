---
title: "GeForce4MX restricted drivers"
date: 2009-11-05
forum: Hardware
---

### Post by oboewan on 2009-11-05
I just did a Wubi install of Karmic. 
Now I'm trying to install my driver for my GeForce 4 MX, and I get the popup saying "downloading and installing drivers," and the progress bar reaches 20% or so, then it stops and I am unable to click Cancel.

EDIT: FIXED!!! YAY!!! The solution was to reboot, go to System > Administration > Software Sources, and uncheck the box in the "Installable from CD/DVD" section. Then it worked perfectly! Turns out that it was trying to install the drivers from the CD even though I had no CD in the drive (or at all). Logged as bug.

---


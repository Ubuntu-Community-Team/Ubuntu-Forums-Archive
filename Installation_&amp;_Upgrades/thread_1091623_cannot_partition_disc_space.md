---
title: "cannot partition disc space"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by Problemswitheverything on 2009-03-09
hi I am trying to install ubuntu using the disc i created. it booted up fine, and when i tried to install to the hard drive i get to the disc partition part and nothing shows up for a hard drive its just blank. there is no drive to click and if i try to hit next anyways it says no root file system. I need help!

---

### Post by taurus on 2009-03-09
Is it a blank harddrive or do you have something (another OS) on it?  

Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That would be a lower case letter L, not number 1.

---

### Post by wpshooter on 2009-03-09
Are you choosing "manual" partitioning ?

---


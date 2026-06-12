---
title: "Dual boot"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by foof on 2005-12-21
I have installed Ubuntu-server and a lot of other apps. Now I want to install WinXP and make a dual boot system on my harddisk afterwards. How can I do this. I have access to partition magic on another (winxp) computer, so I can put my Linux harddrive in that one if it helps?

---

### Post by frodon on 2005-12-21
Just install XP and reinstall GRUB : [http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

### Post by foof on 2005-12-21
But the whole harddisk is EXT3, I guess I have to make room for XP with partition magic first or? Should I resize my linux partition and move it and make room for XP in the beginning of the harddisk space or can I install XP at the end of the disk space?

---

### Post by frodon on 2005-12-21
I think the windows installation will let you create a partition for windows, but in order to gain peace of mind you could indeed create before the windows installation a free partition using partition magic under windows or gparted under linux.
Put your XP partition where you want ;).

---


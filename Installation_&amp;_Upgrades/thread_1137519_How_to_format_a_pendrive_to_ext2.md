---
title: "How to format a pendrive to ext2"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by funky_uncle on 2009-04-25
Shouldn't be a problem, I know. Using GParted I get to delete whatever partitions are on the drive, and add a new one, choosing ext2, which the program apparently does. However, when I look at the pendrive in Nautilus it's listed as ext3, and it has a lost+found folder.

It's a Sandisk Pendrive, and I removed the U3 earlier.

---

### Post by funky_uncle on 2009-04-26
I'm going to try and install CrunchBang Linux to an USB stick (a regular install, not just the live version). I'll probably be running the stick on a lot of different PCs, so I guess I should install a variety of drivers for graphics and wireless cards. But I don't have much of an idea about what's out there and what the most common brands are. nVidia and ATI are the only ones that spring to mind.

Another problem is that I can't seem to get my pendrive formatted to ext2. I've tried using both GParted and the terminal. According to GParted, it does format it to ext2 successfully, but as you can see from the screenshot, Nautilus still sees it as ext3, and there's that annoying lost+found folder that takes up space (what the hell is in that folder anyway, when I've formatted the drive over and over?).
[img]http://img162.imageshack.us/img162/9716/screenshotu.png[/img]
It's a Sandisk Cruzer 4 Gb, and I've already removed that pesky U3 firmware, so it should behave like just another pendrive.

BTW, the reason I want it formatted to ext2 is that it'll probably be a bit faster than other file systems.

---


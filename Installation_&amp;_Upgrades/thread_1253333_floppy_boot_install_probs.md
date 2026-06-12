---
title: "floppy boot install probs"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by dasnshn on 2009-08-30
Trying to install xbuntu on an older machine, P2 350, and need a bootdisc. I have attempted to create a floppy (1.44mb hdd) with the smb.bin to no avail so far.

 Message received is that the Vista formatted disc needs 16.5kb more space to create. The file properties show smb.bin at 1.40mb ( 1,474,560 bytes ). 

Do  you have any ideas/suggestions? 

file path:  Xbuntu9.04 CD>install>smb.bin

---

### Post by lisati on 2009-08-30
If it's just a boot disk you're after, your might want to check out [Smart boot manager]("http://sourceforge.net/projects/btmgr/files/btmgr/3.7-1/")

---

### Post by presence1960 on 2009-08-30
whenever you format any media including a hard disk, flash drive or even a floppy there is always a small amount of space reserved prior to writing to the newly formatted disk. therefore your available space will be slightly less than "advertised". See below screenshot for my floppy properties. Take note of the volume & total capacity readouts. it would appear your file is too large for the floppy.

---

### Post by presence1960 on 2009-08-30
oops forgot the screenshot.

---


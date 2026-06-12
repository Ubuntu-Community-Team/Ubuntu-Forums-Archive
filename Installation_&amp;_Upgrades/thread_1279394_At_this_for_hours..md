---
title: "At this for hours."
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by Torn on 2009-09-30
I need to install Fedora 11, on my my laptop with a dual boot of xp with the In side windows installation of ubuntu.
I know Fedora isnt what you guys do, but these forums have been the biggest help with my experience with Linux.
Currently Each time I try to shrink install with fedora and the live disk, i receive the error Resize failed: 1.
I have re sized the partition in xp, tried again and the installation still shows the whole disk as 1 ntfs partition, when xp tells me different.
I have tried gparted in both ubuntu and fedora, and I am unable to re size the device.
This is getting very frustrating, I need xp for another class, and fedora. Id like to keep everything but if sacrifices need to be made im willing to format and start again.

---

### Post by louieb on 2009-09-30
Can you post a Gparted screen shot? and the output of 
```
sudo fdisk -l
``` lowercase L at the end.  

Just want to see if anything looks strange with your partition table.

---

### Post by Torn on 2009-09-30
Currently reformatting the drive,
but it would just drop down back to the command line.
Nothing would happen.

---

### Post by rreese6 on 2009-09-30
I am assuming you ran fdisk -l from the "command line" in Linux..

---


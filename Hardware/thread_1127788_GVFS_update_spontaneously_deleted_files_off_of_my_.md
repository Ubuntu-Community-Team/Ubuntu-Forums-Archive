---
title: "GVFS update spontaneously deleted files off of my external hard drive?!"
date: 2009-04-16
forum: Hardware
---

### Post by rainwalker on 2009-04-16
I was just about to back up some data to my external hard drive (FAT32), and found that nearly 20 GB of data I had on it (mostly music) had spontaneously disappeared. Gone. Not there.
The folders that contained the files were still there, but had nothing in them, and I would get input/output errors if I tried to copy the stuff back into them/replace them with the folder on my computer. I can only copy the files back if I delete the folder on the hard drive and then make a new one.
I've had problems with slow USB transfers as described [in this thread]("http://ubuntuforums.org/showthread.php?t=793688") and seemed to have gotten it working better (around 2-3 MB/sec), but this is just unacceptable. The only thing I can possibly think of that would cause this were the updates I installed today:
> 
Upgraded the following packages:
chromium-browser (2.0.175.0~svn20090414r13668-0ubuntu1~ucd1~hardy) to 2.0.175.0~svn20090415r13755-0ubuntu1~ucd1~hardy
ghostscript (8.61.dfsg.1-1ubuntu3.1) to 8.61.dfsg.1-1ubuntu3.2
ghostscript-x (8.61.dfsg.1-1ubuntu3.1) to 8.61.dfsg.1-1ubuntu3.2
gvfs (0.2.5-0ubuntu3) to 0.2.5-0ubuntu4
gvfs-backends (0.2.5-0ubuntu3) to 0.2.5-0ubuntu4
gvfs-fuse (0.2.5-0ubuntu3) to 0.2.5-0ubuntu4
libgs8 (8.61.dfsg.1-1ubuntu3.1) to 8.61.dfsg.1-1ubuntu3.2
libgvfscommon0 (0.2.5-0ubuntu3) to 0.2.5-0ubuntu4
libvolume-id0 (117-8) to 117-8ubuntu0.2
tasksel (2.70ubuntu5) to 2.70ubuntu6
tasksel-data (2.70ubuntu5) to 2.70ubuntu6
transmission-common (1.52-0ubuntu0~hardy0) to 1.52-0ubuntu0~hardy1
transmission-gtk (1.52-0ubuntu0~hardy0) to 1.52-0ubuntu0~hardy1
udev (117-8) to 117-8ubuntu0.2
xfonts-scalable (1:1.0.0-6) to 1:1.0.0-6ubuntu0.8.04.1

Please, does anyone have any tips or suggestions or any information at all about what could have caused this and/or what I should do?

---

### Post by cariboo on 2009-04-16
Give [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") a try, to see if you can recover your missing files. Testdisk is in the repositories and you can use Add/Remove Programs or Synaptic Package Manager to install it.

Jim

---

### Post by rainwalker on 2009-04-16
> **cariboo907 said:**
> Give [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") a try, to see if you can recover your missing files. Testdisk is in the repositories and you can use Add/Remove Programs or Synaptic Package Manager to install it.

Jim

I installed and ran testdisk, and after messing with it I'm not quite sure what you're saying I should do...
Also, I finally finished copying stuff back to the hard drive, but I've noticed something peculiar: The "Properties" window lists two different amounts of space filled on the drive (in the same window!), giving me hope that something is recoverable, and the Disk Usage Analyzer gives a slightly different number as well (see screenshot).

I would still like to know what could have happened to cause all this.

---

### Post by bsmith1051 on 2009-04-16
did you try unmounting, then remounting?  Maybe it was a temporary glitch.

---

### Post by rainwalker on 2009-04-16
> **bsmith1051 said:**
> did you try unmounting, then remounting?  Maybe it was a temporary glitch.

Yep, and I tried restarting X, restarting nautilus and rebooting. I plugged it into a Windows machine and the files were gone there, too. The screenshot from above is after I copied everything back, though.

---


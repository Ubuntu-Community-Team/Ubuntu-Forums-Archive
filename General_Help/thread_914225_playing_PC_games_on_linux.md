---
title: "playing PC games on linux"
date: 2008-09-08
forum: General Help
---

### Post by siva_ on 2008-09-08
Hi,

Is it possible to play games on linux, like Call of Duty 4, etc... through software like vmware? Or am I better off creating a separate partition for a windows install?

If I need to create a separate partition, I'm wondering how difficult that will be because I've already dedicated my entire harddrive to ubuntu. Is it possible to resize part of that and use it for windows?

Thanks

---

### Post by jerome1232 on 2008-09-08
Virtual Machines (virtual box, vmware) at this time cannot emulate a 3d graphics card, and if they could it would be very cpu intensive!

One option is wine, if you check the wine database of apps, you'll see cod4 works but you have to compile wine yourself with a patch

[http://appdb.winehq.org/](http://appdb.winehq.org/)

I think the best option if you are into windows only games is dual boot, wine will work but not perfectly and not always.

---

### Post by eriqjaffe on 2008-09-08
edit:  Jerome just said all the same things I did, only he types faster.  ;)

---

### Post by siva_ on 2008-09-12
Hi Jerome,

I've already dedicated my entire harddrive to ubuntu. Is it possible to resize part of that and use it for windows?

Thanks

---

### Post by jerome1232 on 2008-09-12
Yes it is, but when you install windows it will nuke your mbr (grub) there's a good tut in here for restoring grub after a windows install let me find that for ya.

First of all whenever you work with partitions back up your data. 
Even the most experienced of us have regretted typing a command/pushing a button and nuking the wrong drive.

First you will need to boot into a live cd, open gparted (System->Administration->Partition Editor)
Shrink down Ubuntu to the desired size. Windows likes to be the first partition and may throw a fit if it's not so try to move Ubuntu to the end of the drive (not sure if that will work or not) I think windows will be fine as long as it's on a primary partition so don't worry to much about that.
Double check you have everything right.
Apply your changes when sastified.
Reboot, stick in your Windows cd and Run through it's installer, installing to the unpartitioned space we free'd up using gparted.


this is the tut for restoring grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---


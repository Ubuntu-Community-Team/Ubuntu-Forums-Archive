---
title: "Backup files from dead Hard Drive"
date: 2011-09-17
forum: Hardware
---

### Post by Colgax on 2011-09-17
Hey people! I need some help here with my dead hard drive.

Yesterday I was using my computer, got mad at it and hit it where the HD is located. Screen went black and I, scared, switched off the PC. I turned it on again and it wasn't being able to load the Kernel on my Ubuntu partition, but Windows was working fine. I opened Windows and downloaded a Live CD to format the Ubuntu partition and reinstall it.

Today I installed the Live CD content on a USB Pen Drive on Windows and booted on it to see if I could just backup the files from the Ubuntu partition to the Windows one and reinstall it. I did the backup but when I tried to reinstall it the installation crashed. I tried again, but the same thing happened.

On my third try, It couldn't find my HD anymore. the only signal of life it's sending me is on "Disk Utility", where it even show me the volumes, even though they're all listed as Unknown. On "GParted", it doesn't find my HD anymore.

I'm not really interested on backuping all of it. I was going to format it any way. I just need a way to access my files and backup my most important files. Thank a lot for the help! =D

---

### Post by varunendra on 2011-09-18
The most recommended free tool to recover data is "testdisk" or "photorec" (which is just a slightly modified version of testdisk). But I don't think it allows to recover only selected files. It should not be an issue if you have a large enough drive to store the recovered files on.

Also, if you doubt whether the drive is going to stay 'alive' for long, you should create a backup image of it using testdisk. You can later use this image to work upon, instead of the drive itself.

There are also some other tools available, but I have found testdisk quite reliable and capable at detecting and recovering lost data, where even commercial software fail sometimes. So give it a try first. If it doesn't do the job, then tell us if you are interested in commercial ones.

---

### Post by Colgax on 2011-09-18
I'll give it a try and post the results. Thanks! =D

---

### Post by tgalati4 on 2011-09-18
When you got mad at your computer, were you in Windows or Ubuntu?

Grab a large, external, USB drive, load the Live CD, connect to a network, use wired if wireless is not working, open a terminal:

sudo apt-get install testdisk,

man testdisk
man photorec.

Testdisk will try to restore the partitions if the partition table got trashed (which sounds likely).  Photorec will do a sector-by-sector recovery of all recognizable files that you dump to the external drive.

Try testdisk first.  If that can't resurrect the partitions, then photorec.

Don't hit your computer in the future.

---

### Post by varunendra on 2011-09-18
> **tgalati4 said:**
> Don't hit your computer in the future.
^ Else they have a tendency of hitting back really bad :lolflag:

---


---
title: "Camera not mounting"
date: 2008-11-14
forum: Hardware
---

### Post by vaporjourney on 2008-11-14
I've tried a few different options to find my camera listed in the terminal, and I can't find anything.  obviously my Canon won't automount.  I've gone into the terminal with the 'ls /dev/disk/by-label -la' command.  all I got was this:

hearsay@hearsay-desktop:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root 100 2008-11-13 21:49 .
drwxr-xr-x 6 root root 120 2008-11-13 21:49 ..
lrwxrwxrwx 1 root root  10 2008-11-13 21:49 DRV1_VOL1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-11-13 21:49 Ubuntu -> ../../sdb3
lrwxrwxrwx 1 root root  10 2008-11-13 21:49 Video\x20Capture -> ../../sda1

none of these are my camera.

I've also tried a fdisk list command, but got nothing:

hearsay@hearsay-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa882a882

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf778f778

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2534    20354323+   7  HPFS/NTFS
/dev/sdb2            2535        4966    19535040    5  Extended
/dev/sdb3            4967        6878    15358140    7  HPFS/NTFS

I can't find my device listed as being connected thru USB, so I"m not sure how to mount it.  when I connect my Nikon, it mounts no problem.  help would obviously be appreciated.

---

### Post by phidia on 2008-11-14
You can try > lsusb with the camera plugged in and on. If you want provide the model of your canon. 

If it's not recognized though with 8.10 chances are it's not supported. You could use a card reader through the usb system to mount the media instead?

---

### Post by bricedebrignaisplage on 2008-11-15
I'm having something similar here.
Canon IXUS 80 IS
KUbuntu 8.10 (Upgraded recently from Kubuntu 8.04-Kde3.1)

It used to work fine in hardy.
The camera is listed in lsusb and in dmesg. However it's not mounted and not attributed a disk node.

see canon.lsusb.txt attached for detail output of lsusb if of interest.

However, I can access it with digiKam...

---

### Post by pointyblue on 2009-08-02
Hi guys,

Did you find a solution to this problem? My Ubuntu 9.04 doesn't detect a Canon Ixus 85 is.

:-x

---

### Post by pointyblue on 2009-08-02
Figured it out:

The manual said I had to make a specific setting on the camera and then it worked just fine.

---

### Post by bricedebrignaisplage on 2009-12-07
Gosh! I just installed Karmic (fresh install) and I'm having the same problem again. With hardy the camera pops up as soon as I plug it in (no need to configure it), whereas in Karmic it does not. However I can access it with digikam. I installed manually from debootstrap, so maybe a package is missing, but I can't figure which one... (btw, I'm running KDE4).
Any suggestion?

---

### Post by shosto on 2011-07-10
My wife has a similar problem. Her camera is sometimes automounted and others times it isn't. Did some research and came up with a small shell script to use with nautilus to mount it, when automount fails. Instructions are contained in the script itself.

---


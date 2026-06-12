---
title: "Formatting usb hard drive to fat32, need assistance"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by nintennuendo on 2007-07-07
I want to format my usb hard drive to fat32, but the option isn't in the Format list when I right click it in windows.  it 300gb, if that matters.  What should I do?

---

### Post by strabes on 2007-07-07
Install gparted for gnome or qtparted for kde

---

### Post by hardyn on 2007-07-07
if you want to do it in windows, there is a small utility 'fat32format.exe' that will do it.
you may do what was suggested above.
or doing the old hardcore way using fdisk and mkfs

---

### Post by nintennuendo on 2007-07-07
Actually, since it was ntfs, I just installed the NTFS Configuration tool, Can now read and write easy as pie in Ubuntu.  Thanks, NTFS Configuration tool! *thumbs up*

---

### Post by fredj on 2007-07-07
Do it in windows but you don't say which version of windows you have. In XP there is a limit to the size of
fat32 partition you can create, its either 32 or 64 gig, I forget which. You will have to partition the drive first
into multiple smaller chunks. Fat32 disks with a larger partition size than XP allows for fat32 are likely to be
problematic. Also Fat32 files are limited to a 2 gig maximum size (can be a problem if you want to store large
video files).

---

### Post by hardyn on 2007-07-08
they work just fine,

There is no specification restriction with fat32, its simply an MS imosed restriction past 32gb, its simplly to force you into their proprietary file system.

I have been running a 320GB fat32 partion for two years in both ubuntu and windows and it works just fine.

---

### Post by fredj on 2007-07-09
Well it's an interesting idea that MS are trying to force you away from Fat32, I don't think its true. You can
format any size of Fat32 partition you want but I still don't think its a good idea, slow and horribly inefficient.
Fat32 originated in the days when hard disks were much smaller than they are now. Fat32 was originally
a proprietory Microsoft format (and may still be). I still use it on backup drives but never in partition sizes
larger than 32 gig.

---

### Post by hardyn on 2007-07-09
im not going to argue efficiency, but with fat32 you have a lowest common denominator file system; it can be accessed from anything, OSX, Windows98 etc... using a beta driver to access ext3 under windows for ntfs under linux seems like a WAY more sketchy endevour to me.

> 
Although Windows 2000 and Windows XP Professional can mount FAT32 volumes of any size, Windows 2000 and Windows XP Professional can format FAT32 volumes up to 32 GB only. Use NTFS to format larger volumes.

[http://www.allensmith.net/Storage/HDDlimit/FAT32.htm](http://www.allensmith.net/Storage/HDDlimit/FAT32.htm)

---

### Post by OoooMatron on 2008-02-18
Biggest problem with Fat32 is the max file size of 4GB. No good for holding truecrypt or virtualbox containers, for instance.

---


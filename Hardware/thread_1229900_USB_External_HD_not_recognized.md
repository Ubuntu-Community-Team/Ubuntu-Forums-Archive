---
title: "USB External HD not recognized"
date: 2009-08-02
forum: Hardware
---

### Post by frog3764 on 2009-08-02
Here comes another newbie/dummy. My external does show in Gparted but can't recognize it. It is a 320GB Seagate. I found on the site docs - System - Administration - Partition Editor - to label it, but the label is greyed out so I can't do that. Here is the fdisk

Disk /dev/sda: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa82ba82b

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3937 31623921 83 Linux
/dev/sda2 3938 4111 1397655 5 Extended
/dev/sda5 3938 4111 1397623+ 82 Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 38913 312568668 54 OnTrackDM6

All help in the dummy format is appreciated.

---

### Post by dlmarti on 2009-08-02
What kind of partition type is "OnTrackDM6"

If you didn't put that there, I would just fdisk it and be done with it.

---

### Post by frog3764 on 2009-08-03
I didn't put that "OnTrackDM6" there, as there are no partitions on the hd.  What do you mean just fdisk again?  I think I ran fdisk -l to get the screen print mentioned.  I just ran it again and the same report comes up.

---

### Post by dlmarti on 2009-08-03
What I meant was to; delete that partition and create a new one.  The tool I suggested was fdisk.

---

### Post by frog3764 on 2009-08-03
There are no partitions on the hard drive, which is full of back-up files from XP.  I want to use this external for all my downloaded files to back up my other pc (two pc's)  which is using XP.  My zip files are the only files needed to keep from Ubuntu, so I assume Ubuntu will be able to move these to the external OK even though there are other types of files there that it can't read.  I can make a Linux partition for those files too, but I would like for XP to be able to pull them out if I ever need them for the other pc or this one if I ever go back to Windows.  I hope you guys can follow this mess.  My immediate problem here is to get this external to be recognized by Ubuntu.   Now what?

---

### Post by dlmarti on 2009-08-03
Linux is not going to mount the drive until it is properly partitioned and formated, which it clearly is not (from the fdisk -l ouput).

---

### Post by frog3764 on 2009-08-03
OK, so can I make a Linux partition without disturbing the current XP files that are there?  I don't want to lose anything.  Will the XP pc be able to still read the external if I ever use it there?

---

### Post by dlmarti on 2009-08-03
As far as I can see, no data is on the drive, unless XP knows how to read that weird partition type that I have never heard of.

---

### Post by frog3764 on 2009-08-03
I just plugged in the external to the XP and the files are all still there with 170gb free out of of 320gb.  The Linux PC still won't find it when I plug it in.

---


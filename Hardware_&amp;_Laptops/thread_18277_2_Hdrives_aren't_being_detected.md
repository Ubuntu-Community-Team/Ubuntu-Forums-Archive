---
title: "2 Hdrives aren't being detected"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by Mark7805 on 2005-03-05
My 2 Hard Drives aren't being detected.Only my cd drives are

---

### Post by bored2k on 2005-03-05
[QUOTE=Mark7805]My 2 Hard Drives aren't being detected.Only my cd drives are[/QUOTE]
 [http://www.ubuntuforums.org/showthread.php?t=18273](http://www.ubuntuforums.org/showthread.php?t=18273)

---

### Post by Mark7805 on 2005-03-05
I don't understand anything in that guide.Can some1 plz tell me exactly what to do?

---

### Post by doitashimashite on 2005-03-05
I need more information. "Two harddrives" aren't being detected. How many harddrives do you have? Are you booting from a live CD or is at least one harddrive detected (i.e. the one you boot from)?

---

### Post by Mark7805 on 2005-03-05
2 hard drives I have
My CD-RW and CD-Rom is detected 
I'm using the real version.NOT LIVE

---

### Post by doitashimashite on 2005-03-05
So, if I understand this correctly, you have two harddisks, and none of them is detected... And you don't run a live CD.

Does this mean that you have a problem installing Ubuntu?

---

### Post by Mark7805 on 2005-03-05
No.I have it fully installed.I just go to Computer then Disks and I don't see any hard drives.Just my CD-rw,CD-rom,floopy and file system

---

### Post by doitashimashite on 2005-03-05
Ah, I see.

Well, the Ubuntu disk should be there, saying "filesystem".

The other one is probably not mounted.

$ sudo mount

Will give you a list of the mounted partitions.

---

### Post by Mark7805 on 2005-03-05
This is what it says```
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdb1 on /mnt type ext3 (rw)

```

---

### Post by doitashimashite on 2005-03-05
This is not right. The first partition of the primary slave is mounted TWICE!
You should at least remove the last entry:

/dev/hdb1 on /mnt type ext3 (rw)

And I'd like to see what

$ sudo fdisk -l /dev/hda

shows.

---

### Post by Mark7805 on 2005-03-05
It says this ```
Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4862    39053983+   7  HPFS/NTFS

``` and how do I remove a entry?The Last one you want me to remove.

---

### Post by dikki on 2005-03-06
For example: sudo nano /etc/fstab and then remove it.

---

### Post by doitashimashite on 2005-03-06
Yes, and after next boot you should check with

$ mount

to make sure nothing is mounted under /mnt anymore.

Then you can mount the filesystem on your first disk under /mnt:

$ sudo mount /dev/hda1 /mnt

But! Since this is an NTFS filesystem, it will be mounted read only.

---


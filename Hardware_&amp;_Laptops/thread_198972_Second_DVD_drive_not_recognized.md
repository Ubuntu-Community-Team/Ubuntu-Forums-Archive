---
title: "Second DVD drive not recognized"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by igknighted on 2006-06-18
I just switched to Ubuntu and installed dapper, and for some reason the DVD drive I install from (whichever I used to install, I've tried both) works perfectly, and the other won't show up at all.  Any suggestions?  Am I missing a step somewhere?  Everything else has worked like a charm, so I'm a bit puzzled.

---

### Post by cotcot on 2006-06-18
Was the second disk drive recognised with the OS you used before Dapper ?

---

### Post by igknighted on 2006-06-19
yes, the drive worked fine with Windows.  And I have had both drives working, just not at the same time.  It only recognizes the one I install from.

---

### Post by lazyd2 on 2006-06-19
Is it in your */etc/fstab*?

---

### Post by igknighted on 2006-06-19
[QUOTE=lazyd2]Is it in your */etc/fstab*?[/QUOTE]

no, it is not in the fstab.  All that is there are my 2 hard drive partitions - hda1 and hda5 (swap) - and the first DVD drive hdd

---

### Post by Ocxic on 2006-06-19
add this line to your /etc/fstab:

(could be hdc or hde depending on your setup, prolly hdc try that one first.)

```

/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

then 

```

sudo mkdir /media/cdrom1

```

And reboot, then both drives should work

---

### Post by igknighted on 2006-06-19
I tried this and was told it could not mount because the folder /media/cdrom1/ was not there.  I created this folder, now I get:

mount: special device /dev/hdc does not exist

I can now see that the drive is there, it just wont mount.

---

### Post by Ocxic on 2006-06-19
post the output of /etc/fstab and, sudo fdisk -l

---

### Post by igknighted on 2006-06-19
Here's the fstab:

[QUOTE=fstab]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
[/QUOTE]

And the fdisk readout:

[QUOTE=fdisk]Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14409   115740261   83  Linux
/dev/hda2           14410       14596     1502077+   5  Extended
/dev/hda5           14410       14596     1502046   82  Linux swap / Solaris

Disk /dev/sda: 5007 MB, 5007744000 bytes
255 heads, 63 sectors/track, 608 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131    0  Empty
/dev/sda2   *           6         608     4843597+   b  W95 FAT32
[/QUOTE]

The FAT drive is  my ipod

---

### Post by lazyd2 on 2006-06-19
It may be a long shot, but have you tried rebooting?

---

### Post by Ocxic on 2006-06-19
one last thing post the output of "lshw" please

---

### Post by igknighted on 2006-06-21
haha, thank you all so much for the help, I finally fixed the problem today when I opened the case to see if I had any more space for another hard drive... and discovered that the cable out of the DVD drive in question was pulled out.  So after plugging in the IDE cable, the drive works fine.  Again, thank you for the time.

---


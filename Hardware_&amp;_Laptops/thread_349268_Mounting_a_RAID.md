---
title: "Mounting a RAID"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by SpudDogg on 2007-01-29
I'm looking to mount a RAID set consisting of 2 250GB SATA drives.  There is a filesystem on them, NTFS.  I will need Ubuntu to see this as a single 500GB drive, as that is how I always had it set up in my Windows days.  Does anyone know if this is possible?  

My RAID controller is on-board on my ASUS MB, and the RAID was done from the BIOS not from within Windows.

Any help would be GREATLY appreciated!!  If I cannot get this working I'll have to go back to Windows until I can afford some single drives big enough to do what I need (which I REALLY don't want).

Here is the output of fdisk -l:

```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/hda2           12749       30400   141789690    f  W95 Ext'd (LBA)
/dev/hda5           12749       13827     8667036   82  Linux swap / Solaris
/dev/hda6           13828       30400   133122591   83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488392033+  42  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
```

I need sda and sdb as one drive mounted to /mnt/T


And here is my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=fb8abd35-287d-4e91-9756-88abbec6573b /               ext3    defaults,erro$
# /dev/hda5
UUID=bfc9553b-dbcf-4ef3-b881-12c143338416 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc1       /mnt/U    ntfs-3g    defaults,locale=en_US.utf8   0  0
```

Can someone help?

---

### Post by SpudDogg on 2007-01-30
Can someone please help?

---

### Post by RandomJoe on 2007-01-30
Can't help you with getting that specific setup working again in Linux, my suggestion would be to back everything up elsewhere (assuming you have space, of course!) then create a new RAID with the drives under Linux (using software RAID) and move the data back.

As far as getting the original setup working, if the mobo's RAID was true hardware RAID then it should present the drives as a single logical drive to Linux.  But most mobos use "Fake RAID" - where they rely to a lesser or greater extent on a driver in the OS.  Some are supported in Linux, but I don't know anything about them - I just use Linux's software RAID instead.  

If yours is supported it's *possible* getting the appropriate "Fake RAID" driver loaded would allow you to see that array okay.  But I wouldn't be surprised to find it still needs to be reformatted due to differences between the Windows and Linux driver...

---

### Post by SpudDogg on 2007-01-30
Yes, my motherboard is definately a "fake" raid.  It's the Silicon Image whatever.


If I understood what you said, it sounds like I should be able to turn off my bios raid and just do it in linux...But then if I ever do need to boot into Windows, it will not read that drive...Is that correct?  Also, can linux create NTFS on a drive?


Thank you for the reply.

---

### Post by RandomJoe on 2007-01-31
Yes, Linux can do the RAID for you without any chipset support.

No, Windows can't see that RAID.

And AFAIK Linux can't create NTFS partitions.  It can barely write to them!

If you need to be able to access the RAID from both OSes, the best bet would probably be to try getting the "Fake RAID" support going and see if both can see the RAID properly.  I've never tried using it, so I don't know if that'll work - my guess would be there are going to be just enough differences in implementation that it won't.

If you _do_ get it readable from both, you'll have to think about what filesystem you use.  If you intend to write to it in Linux, I would suggest using FAT32.  Linux support for FAT32 is far more mature than NTFS.  Last I heard for sure, NTFS write support is still only to the point of changing data within an existing file, and it can't change the size of the file.  Not exactly useful in general terms!

Okay, did a little Googling - it appears 'dmraid' is what supports the software/Fake RAID sets.  Here is the [manpage for it]("http://www.linuxmanpages.com/man8/dmraid.8.php") and it does mention Silicon Image "Medley".  It isn't installed on Ubuntu by default - and is in the Universe repository.

---


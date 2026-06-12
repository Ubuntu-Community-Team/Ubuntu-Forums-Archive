---
title: "IDE Raid drive does not appear in Ubuntu"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by fowie on 2007-12-12
I just finished building my new system with an Aopen i975Xa-YDG.  I had to upgrade the BIOS before I could even get Ubuntu to work because the motherboard has one primary IDE slot and then two IDE RAID capable slots.  Now Ubuntu is working fine installed on the second partition of my HD on the primary IDE port, but it can't see any of the hard drives connected to the RAID IDE ports.  Any idea where I should start in trying to figure this one out?  I'm dual-booting with Vista installed on the first partition of the primary HD, and Vista can see all of the drives on the RAID IDE ports just fine.  (Who'd have though, windows working when linux won't?  Crazy, I know!)

---

### Post by fowie on 2007-12-22
Ok, the first answer is found in [this post]("http://ubuntuforums.org/archive/index.php/t-431781.html").  

Here's my current issue.
I've compiled my own kernel with the it821X IDE drivers instead of the SATA/PATA drivers, and it sees my raid 0'ed drives just fine.  fdisk -l returns this:
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b151b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3037    24393678+   7  HPFS/NTFS
/dev/sda2            3038        4756    13807867+  83  Linux
/dev/sda3            4757        4865      875542+   5  Extended
/dev/sda5            4757        4865      875511   82  Linux swap / Solaris

Disk /dev/hda: 160.0 GB, 160052674560 bytes
255 heads, 63 sectors/track, 19458 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007997c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19458   156296353+   b  W95 FAT32

```
(The raid is /dev/hda)
I actually used gparted to make the /dev/hda1 into a fat32 partition.  Here's my problem though, when I go to mount the device I get this error:
```

 sudo mount -t vfat /dev/hda1 /Striped/
mount: special device /dev/hda1 does not exist

```

a little more info with some verbose options:
```

sudo mount -vvvt vfat /dev/hda1 /Striped/
mount: fstab path: "/etc/fstab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: no LABEL=, no UUID=, going to mount /dev/hda1 by path
mount: spec:  "/dev/hda1"
mount: node:  "/Striped/"
mount: types: "vfat"
mount: opts:  "(null)"
mount: mount(2) syscall: source: "/dev/hda1", target: "/Striped/", filesystemtype: "vfat", mountflags: -1058209792, data: (null)
mount: special device /dev/hda1 does not exist

```

Any idea where I should go from here?  Even pointing me to some log files with more information would be useful right now...

---

### Post by fowie on 2007-12-22
Fixing one problem to find another.  I uninstalled dmraid and mdadm and now I can mount the drive.  However, after copying a few files onto the drive I get 
```

cp: writing `/destinationfile': Input/output error

```

I've tried using an NTFS file system on the raid drives and a vfat system (I need to read it in Windows) and the same error happens.
how can I find out what's wrong?

---


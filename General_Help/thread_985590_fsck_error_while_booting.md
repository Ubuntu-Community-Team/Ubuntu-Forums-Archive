---
title: "fsck error while booting"
date: 2008-11-17
forum: General Help
---

### Post by mooncaptain on 2008-11-17
I recently removed a disk from my system and rebooted and got an error while booting so I hooked the drive back up and started up again. Then I unmounted the drive and rebooted and got another similar but different error while booting.

Here's the log of that error from /var/log/fsck/checkfs
```

Log of fsck -C3 -R -A -a 
Mon Nov 17 18:32:23 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sdb1 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Mon Nov 17 18:32:24 2008
```

every time I get the error the boot process stops and I have to type ctrl-D to continue. Any idea how to repair this problem?

---

### Post by Yellow Pasque on 2008-11-17
Please post output of:
```
cat /etc/fstab
sudo fdisk -l
blkid
```

---

### Post by mooncaptain on 2008-11-17
> **Temüjin said:**
> Please post output of:
```
cat /etc/fstab
sudo fdisk -l
blkid
```

```
paul@ubuntu02:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=11354c26-945f-4b1c-a9ba-4c9936ff83e0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=336f139e-7166-47d3-8384-943b46d82e09 none            swap    sw              0       0
/dev/sdb1  /media/disk-3  ext3  rw,nosuid,nodev  0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

paul@ubuntu02:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ccd2289

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4142    33270583+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e3f3ed9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4679    37584036   83  Linux
/dev/sdb2            4680        4866     1502077+   5  Extended
/dev/sdb3            4867        9729    39062047+   b  W95 FAT32
/dev/sdb5            4680        4866     1502046   82  Linux swap / Solaris


paul@ubuntu02:~$ sudo blkid
/dev/sda1: UUID="30F46E33F46DFC0A" LABEL="System" TYPE="ntfs" 
/dev/sdb1: UUID="11354c26-945f-4b1c-a9ba-4c9936ff83e0" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="336f139e-7166-47d3-8384-943b46d82e09" 
/dev/sdb3: UUID="4920-C644" TYPE="vfat" 


```

---

### Post by Yellow Pasque on 2008-11-17
It looks like your system swapped /dev assignments when you removed/inserted the drive (this is why we use UUID's in fstab). As it is now, you're trying to mount your NTFS partition as an ext3 device:

Backup your fstab and open it for editing:
```
sudo cp /etc/fstab /etc/fstab.old
gksudo gedit /etc/fstab    ;or use kdesudo kate for KDE/Kubuntu
```

Change the line reading "/dev/sdb1  /media/disk-3  ext3  rw,nosuid,nodev  0 2" to:
```
UUID=30F46E33F46DFC0A  /media/disk-3  ntfs-3g users,uid=1000,gid=100,fmask=0113,dmask=0002,locale=en_US.utf8  0  2
```
Save. Quit. Reboot.

---

### Post by mooncaptain on 2008-11-17
Thanks, that did the trick. Just so I can come away from this with a little knowledge I "mounted" the vfat drive, which I couldn't see before, by adding the following to the fstab file:

```
UUID="4920-C644" /media/disk-4 fat32
```

I left off all the attributes except for the UUID the mount point and the drive type because they were the only ones I really understood. The drive is now visible, readable and writable from Linux.  Is there anything that may be essential for a data drive that I want to share between my Ubuntu system and the dual boot XP system?

What man page, or link would give me details on the rest of the parameters?

Thanks again,
mc

---

### Post by Yellow Pasque on 2008-11-17
Look at man mount [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)
For FAT32, the filesystem type you want in your fstab line is "vfat" (not fat32).
In the man mount page, there is a section for options for all filesystem types and option sections for specific filesystems (see fat and vfat).

---


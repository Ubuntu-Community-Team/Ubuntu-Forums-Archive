---
title: "[SOLVED] Mounting at Startup"
date: 2008-09-17
forum: General Help
---

### Post by RobOrr on 2008-09-17
So i've been faffing around trying to get my NTFS partition to mount automatically when i load ubuntu, and I also can't find an adequate solution with the search tool. Read/write is perfectly fine, I just have to mount manually each time i start up. Kindof irritating, especially when all my music is stored on the NTFS partition. Is there a checkbox / option that i havent discovered, or is it back to terminal? Help would be appreciated!
This is on Heron by the way.

---

### Post by iaculallad on 2008-09-17
Try to post whatever displays when you issue the commands below on your terminal:

```
sudo blkid
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Elfy on 2008-09-17
Install ntfs-config and there will be a tool in system tools which you can use to mount the drive at boot - it gets added to fstab

```
sudo apt-get install ntfs-config
```

You'll need to reboot - you can see the changes it has made ```
cat /etc/fstab
```

Some reading if you like -

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)


Is that southampton as in soton?

---

### Post by kosmiciatakuja on 2008-09-17
This might be something you checked already in the first place, but just in case you didn't, look into /etc/fstab file. I believe there should be an 'auto' option in there for your NTFS filesystem for it to be mounted on boot. 

Here's a bit more in-depth howto on fstab:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If you did and it still doesn't mount, maybe read through dmesg just after booting to see if it at least tried.

---

### Post by RobOrr on 2008-09-17
blkid returns:
/dev/sda1: UUID="9E78AF4778AF1D51" TYPE="ntfs" 
/dev/sda5: UUID="8c2852af-aab0-453a-9e2e-07bc656b689d" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="50123c8c-1551-4ce3-b24a-3a2181ebac70" 

fdisk -l returns:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b3d8b3d
and finally:

   Device Boot      Start   # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8c2852af-aab0-453a-9e2e-07bc656b689d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=50123c8c-1551-4ce3-b24a-3a2181ebac70 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
      End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       14593    14819962+   5  Extended
/dev/sda5           12749       14510    14153233+  83  Linux
/dev/sda6           14511       14593      666666   82  Linux swap / Solaris

I have also found that it's mounting the NTFS partition in /media/disk, i.e. as a removable drive.  I think this may have something to do with it, but my distinct lack of knowledge lets me down here.

---

### Post by RobOrr on 2008-09-17
Thanks for all replies - using the fstab guides you gave me i manually inputted the line:

# /dev/sda1 
UUID="9E78AF4778AF1D51" /media/windows	ntfs-3g defaults,locale==en_GB.utf8 0 0

and it's all working grand.

(the # /dev/sda1 is just to remind me which bit is which, it's not code.)

and yeah southampton as in soton, am at university there, but taking leave of absence till end of january due to illness, so staying at mums house in staffordshire doing little and using computer lots :D

---


---
title: "intermittent cd-rom automount failure"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by ekarni on 2006-06-23
My LiteOn 1633 CD/DVD-RW drive is misbehaving since I upgraded to Dapper.  (Worked fine under Breezy a week ago).  When I insert a disc, it usually fails to mount (no icon on desktop, nothing showing in Nautilus).  I don't hear the drive spin up as usual, the activity LED stays off, and it is usually slow/non-responsive to the eject button.  Also, the mouse sometimes hangs for a few seconds/system feels momentarily non-responsive.  top does not show anything hung up or otherwise abnormal.    

To make things even more interesting, after a few "insert disc - nothing - eject" cycles, it sometimes mounts fine.  In the case of a DVD, playback is slightly jerky.  This is also new compared to Breezy.

Any ideas on things to try are appreciated.  Here's some info to get started:
MSI K8T Neo2 Motherboard, 1GB Ram, Athon64 3000+ Socket 939
Ubuntu Dapper 6.06, dist-upgraded from Breezy a week ago
2.6.15-25-386 kernel (tried K7 but it caused problems)
NVIDIA FX5700LE video card, nvidia graphics driver

```

$ hdparm /dev/hdc
/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext2    defaults        0       2
/dev/hda8       /home           ext3    defaults        0       2
/dev/hda7       /tmp            ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```

Thanks!

---

### Post by ekarni on 2006-06-25
Bump!  Anyone?

---

### Post by ekarni on 2006-07-01
For anyone finding this thread on a search, the problem was enabled DMA on the CD drive.  Ref on the topic: [https://help.ubuntu.com/community/DMA]("https://help.ubuntu.com/community/DMA")
just use -d0 (DMA off) instead of -d1 (DMA on).

When (re-)installing from the alternate CD and this problem is suspected, hit F6 and add [i]ide=nodma[i] to the boot options.

---


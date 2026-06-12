---
title: "CD-ROM will not automount - 7.04"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by FogOgg on 2007-04-26
I just installed 7.04 alternate yesterday on an older piece of equipment ( 800mhz Celeron, 512mb). Everything works great except cdrom will not automount.

I have googled all over, combed this forum, although I will admit my forum scouring was not as thorough as my search engine clicking. So far the only thing I've seen dealing with this solves the problem simply by commenting out the cdrom line in fstab.

That doesn't work for me and I've been left to my own devices to figure this out. If it were my machine I wouldn't care, mounting manually doesn't bother me, but it's for a coworkers 72 year old mother and I think she would appreciate simplicity.

I did try swapping out my cd drives as dmesg provided some odd messages concerning it. Something along the lines of "slow to respond". That cleared up the dmesg issues and it appears clean to me now. If anyone cares to take this on I will provide any information neccessary.

I also attempted reinstalling hal and all of it's dependencies for fear of a corrupted install cd. I downloaded and installed several packages to no avail. Hald IS running when I "ps" for it, and "lshal --monitor" shows state changes in the drive when I insert and remove discs.

I also attempted to fiddle around with groups and group settings a little as I saw that /dev/scd0 belonged to root/cdrom. Naturally I HAVE checked in Preferences->Removable Drive and Media to make sure that automounting is enabled.

At this point I'm left with :confused: :confused: and am posting here looking for any help I might be able to find. Thanks. 


fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=51801127-98b0-4067-b547-3bd1b1357c5a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=9d4862ac-4e79-422c-8932-0fc5e91cb728 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

dmesg snip:
[   24.347794] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   24.347918] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   24.843475] ata2.00: ATAPI, max MWDMA2
[   24.864845] FDC 0 is a post-1991 82077
[   25.007328] ata2.00: configured for MWDMA2
[   25.012025] scsi 0:0:0:0: Direct-Access     ATA      ST320413A        3.39 PQ: 0 ANSI: 5
[   25.013577] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SM-308B T100 PQ: 0 ANSI: 5

---

### Post by Robin T Cox on 2007-04-27
In your fstab line -

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

I think your 'noauto' should be 'auto'.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by FogOgg on 2007-04-27
Thanks for your reply, but all that did was make a cd currently in the drive mount automatically at boot.

Also thanks for the link, it lead me around and I learned about user options and fstab configuration, however, it ended in a dead end for me. I think my issue may be permissions related, but I can't figure out what permissions or ownerships to alter. I attempted giving my user and group ownership of the device and mount point. Also, I tried I tried giving full access of the drive and mount point to all users.

Both solutions failed. Giving ownership of the mount point, all links to it and /dev/scd0 to haldaemon:cdrom was met with similar failure. 

Why should this be so difficult. I hear so many accolades for this distribution claiming ease of use and how exceptional it is for beginners, yet I find myself wondering how something as simple as automounting the cdrom can be overlooked on the release CD?

---


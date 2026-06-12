---
title: "DVD CD Rom Drive problems Ubuntu 11.04 64 bit"
date: 2011-09-04
forum: Hardware
---

### Post by sellingandbuyingmusk on 2011-09-04
I installed Ubuntu Ubuntu 11.04 64 bit, but had Windows 7 64bit and thought to give this new OS a try.  The problem is when i installed Ubuntu 11.04 64bit It did not see the My Dvd CD Rom drive at all  where its suppose to be located and then mount it. How can I install this Drive and then mount so i can use it. If can least use some of the drive, but right now there is nothing which it not reorganizing the drive.

If anyone can help me out either by info or steer me in the right direction to find the information to solve this problem. Thanks!

Drive Info: Liteon, DVD Writer with light-scribe direct, Seral ATA
Model# LH 20A1L06C

---

### Post by V4hid.ir on 2011-09-10
I have same problem with Ubuntu 11.04 32bit and samsung sata DVD writer.
how can i slove that and mount dvds?

---

### Post by mon_r on 2011-09-11
Same here.

I tried the command to mount and get the same results.

$ sudo mount /dev/sr0 /media/cdrom
mount: mount point /media/cdrom does not exist

$ sudo mount /dev/scd0
mount: can't find /dev/scd0 in /etc/fstab or /etc/mtab

using the command
$df
the cd drive does not show. Only the HDDs.

and the location of the cd on the hard drive does not exist.

I have a dual-boot and the 10.04 ubuntu does detect and auto-mount it with no problems.

---

### Post by Volker74 on 2011-09-11
This seems to be the same problem as in 

[http://ubuntuforums.org/showthread.php?t=1837273&highlight=dvd+rom+drive+support](http://ubuntuforums.org/showthread.php?t=1837273&highlight=dvd+rom+drive+support)

Sorry to say that no answer has emerged there either. Maybe the threads should be merged ? (admin?)  Just saying. 

Anyway, I  have the same problem and am lacking an answer :(.

Regards

Volker

---

### Post by mon_r on 2011-09-11
[B]As well as these threads:

mount point media/cdrom0 does not exist[/B]
[http://ubuntuforums.org/showthread.php?t=1484007](http://ubuntuforums.org/showthread.php?t=1484007)

 ** 	[SOLVED] mount point /media/cdrom does not exist  **
[http://ubuntuforums.org/showthread.php?t=1496484](http://ubuntuforums.org/showthread.php?t=1496484)

Last one is misleading as it does not show any solution.
What changed since 9.10?

---

### Post by Sirolf10 on 2011-09-24
Hello,

I had the same problem. When I first got my computer, I also had problems with installing Ubuntu from a disk. After changing a BIOS setting EDI to AHCI, it worked back then. When I looked at that setting again today, I discovered that it was back on EDI again, probably because of a BIOS-update.

Now I've changed it back again from EDI to AHCI and I can read disks again. I hope this solves it for you to!

Good luck!

---

### Post by mon_r on 2011-10-07
I think it's a typo: IDE not EDI
I tried that and it didn't work for me. Actually it got worse, it stopped booting from my main HD which contains 11.04's grub even if the boot sequence is configured to boot from that.
ADHI is used if you are planning on using RAID and have multiple HDDs.
But before that - in IDE mode, the BIOS already detects the DVD drive, so I'm guessing that it is only the OS that doesn't detect the DVD drive.
I'll do more tests in the future after a few more research.

---

### Post by enfoque on 2011-10-08
I have the same problem. Please let me know if you solve it. Thank you very much!

---

### Post by mon_r on 2011-10-14
Upgraded to 11.10. Works fine now. :D

---

### Post by mon_r on 2011-10-14
Just upgraded to 11.10. Works fine.

---


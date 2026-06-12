---
title: "Cant's spindown my Samsung HD103SI &amp; HD103UJ"
date: 2009-08-05
forum: Hardware
---

### Post by MADevil666 on 2009-08-05
Hello, 

I expose my problem: 

I have hard drives for storage in a PC, and I rarely reaches there, so I spindown normally my data disks after 20 minutes. 

Only problem with the last 2 I have installed, it no longer spindown (standby or sleep). 

I used the dual method; in the config hdparm.conf and in rc.local (with my hdparm-S 240 / dev / sdx) 

I have 2 other 500GB samsung drives that go into standby without problems, and another 2 seagate 500 too. 

I checked if there was no activity after a spindown (hdparm-y / dev / sdx) in the dmesg with the following method 
 - echo 1 > /proc/sys/vm/block_dump to activate the debugging of the kernel on the disk 
And nothing writing on it. 

When you do a hdparm-Y (sleep) and immediately after hdparm-C, it displays *standby*, then it immediately returns to *active / idle* 

There are good that this bug is supposed to be corrected in my version (I'm Karmic dev, so hdparm 9.15) 
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/388506](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/388506)
[http://ubuntuforums.org/showthread.php?t=969792](http://ubuntuforums.org/showthread.php?t=969792)
indeed, it uses blkid instead of vol_id but for the same final result (it's not asleep ...) 
So I changed the udev rules file and restart udev, same. 

I also tested on another sata controller (instead of marvel promise), same effect. 

Off the APM and ACPI, checked in the bios that I had not an option for that in the former. 
 
I also tested from a live cd (e17 Elive-compiz) with kernel 2.6.26.8 (for those who would criminalize my kernel Karmic) 

If someone has an idea, I'm interested. 

In advance thank you. 
PS: The other labels of the HDDs are SpinPoint F1 and Ecogreen F2

---

### Post by zengl on 2009-08-31
Can you try a spindown time of 10min?

I have two **HD103SI **in a software RAID for a data-only partition. Setting the spindown time to 10min works fine to get them spin down, as well spinning them down manually. Using higher values for the spin-down time, e.g. 20min does not work at all.

---

### Post by lmester on 2010-12-10
I had the same problem and got my HD103SI to spin down after setting advanced power managment to 253. 
 
It was set to 255 and values above 253 won't let it spin down.
 
hdparm -B253 -S12 /dev/sdb
 
I tried this on another HD103SI in the same box and on the same SATA controller and it would not spin down. I reset the drive to defaults and then it worked. Also, I should have checked the hdparm man page first :-(.  An hdparm -B setting above 127 should not allow the drive to spindown. -B 253 is working for me.  I have no idea why.

---


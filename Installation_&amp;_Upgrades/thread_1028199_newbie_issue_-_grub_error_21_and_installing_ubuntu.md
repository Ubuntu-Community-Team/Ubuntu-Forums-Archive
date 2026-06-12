---
title: "newbie issue - grub error 21 and installing ubuntu on 2nd harddisk for first time"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by evildaifu on 2009-01-02
Hi Guys,

Just wanted to let you guys know of something that I have resolved when I got Error 21 with grub v1.5 after installing ubuntu v8.10 for the first time on my 2nd harddisk (1st harddisk was running a Windows operating system and I installed it first).  This is a common scenario for newbies I reckon to have had Windows installed on the 1st hdd then maybe have a 2nd hdd lying around and wack that in then maybe decide to load linux on the 2nd hdd).

I've read that it is easier to have the bootloader done by linux and this is the case I reckon (since Windows does not allow you to do this easily except if you decide to run something like Partition Magic which costs $$$).

So, I had to do 2 things.  Firstly, using ubuntu live, run gparted and flag the linux ext3 partition in the 2nd hdd as the boot hdd.  Secondly, go into my Dell Dimension 4300 BIOS CMOS settings and have it recognise the Primary Disk 1 (i.e. 2nd hdd since the 1st hdd was already recognised as Primary Disk 0) as a harddisk by using autodetect to detect the hardware.  The detection still came back as "unknown" but it worked.

So now, grub v1.5 comes up without having to reconfigure it and gives me the choice to successfully boot up into ubuntu v8.10 or windows 7

Hope this helps someone else one day :D

---


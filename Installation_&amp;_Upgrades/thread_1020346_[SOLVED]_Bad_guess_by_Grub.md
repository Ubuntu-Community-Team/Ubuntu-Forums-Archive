---
title: "[SOLVED] Bad guess by Grub"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by pcal on 2008-12-24
Hi folks - and Merry Christmas to you all.

I have just installed Ubuntu on a clean partition occupying the 2nd half of a sata drive in a new machine (xp is on the first half). There is also another pata drive in the system temporarily, which also has xp installed on it just for transfering its user files and settings to the new machine.

Anyway, Ubuntu put grub on the mbr of the pata drive (c: ) rather than the sata drive (i: ). I need to remove grub from the pata drive altogether, and install it to the sata drive instead.

As my linux skills are still at the developmental stage, I'm hoping someone can point me to a simple "step by step" to achieve this... please?

Thanks in anticipation.

Pcal

---

### Post by logos34 on 2008-12-24
See link Restore Grub in my signature below.

Before you boot the live cd, power off the computer and disconnect the IDE/pata drive.  

Now boot the live cd and reinstall grub.  Afterwards turn off the computer again and reconnect the IDE drive.   Turn on and go into the Bios...make sure the SATA is first in the Hard Disk boot priority, ahead of the IDE.  Boot into Ubuntu.  You can remove Grub bootloader (stage1/1.5) from the MBR of the IDE drive using Super Grub Disk 'uninstall' option (see link my sig).  There's also a [dd command]("http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/") you can run.

---

### Post by caljohnsmith on 2008-12-24
Although disconnecting the PATA drive is a way to guarantee that Grub won't be installed to it, I don't think disconnecting the PATA drive is really necessary in order to install Grub to the SATA drive as long as you are a little careful. :) To install Grub to the MBR (Master Boot Record) of your Ubuntu SATA drive, first boot your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Next, to restore a Windows MBR to your PATA drive, you could boot your Windows Install CD, go to the "recovery console" and run:
```
fixmbr
```
And that should work. Or if you don't have a Windows Install CD handy, you can instead use the Ubuntu Live CD to install a Windows equivalent MBR by first doing:
```
sudo fdisk -l
```
Using that output, decide if your Windows HDD is drive sda or sdb, and then do:
```
sudo lilo -M  /dev/[COLOR="Blue"]sda[/COLOR] mbr
```
And change "sda" above to sdb if your Windows is actually on drive sdb. How about giving that a shot and let us know how it goes, or let me know if you run into problems.

---

### Post by logos34 on 2008-12-24
> **caljohnsmith said:**
> Although disconnecting the PATA drive is a way to guarantee that Grub won't be installed to it, I don't think disconnecting the PATA drive is really necessary in order to install Grub to the SATA drive as long as you are a little careful. 

I think the manual way makes perfect sense in this case (all you need to do is unplug the power cable on the hdd)...leaves no room for doubt and, in my experience, saves time in the end.

---

### Post by pcal on 2008-12-26
Thanks guys! Now that the "relly rush" is over for this season, I will have a go at making these changes today and let you know how it goes...

Cheers.

---

### Post by pcal on 2008-12-26
Worked first time. Thanks heaps...

Regards,

Pcal

---


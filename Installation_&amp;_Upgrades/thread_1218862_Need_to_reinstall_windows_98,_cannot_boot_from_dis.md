---
title: "Need to reinstall windows 98, cannot boot from disk."
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by tomasrey88 on 2009-07-21
Hi,

I messed up the disk partitioning and deleted my windows 98. I need to reinstall windows 98 over my ubuntu, then reinstall ubuntu with the partition done right for dual operating system on one hard drive.

However, no matter what bios setting I choose, I cannot boot from the cd rom. My bios is messed up. Is there another way to reinstall windows 98? Can I type in a command into grub to boot from cd? If so, what commands do I type? 

Answer my question and I will mail you a free Michael Jackson CD or Elvis CD (your choice). I can also assist you with schematics and help with your rife project. I have built a zapper with contact pads, a doug electromagnetic coil, and a plasma tube rife machine. 

Thanks,
:P

---

### Post by djdarrin91 on 2009-07-21
Rough spot for sure.is booting from usb an option?

---

### Post by mister_p_1998 on 2009-07-21
I think you need a boot floppy, dont think 98 can boot from CD can it?
you'll need to run fdisk in dos to erase all non-dos partitions.
Steve

---

### Post by tomasrey88 on 2009-07-21
Does this mean that I will have to make over 100 floppies to install win 98 as win 98 is over 100 MB? Each floppy is over 1 MB. Or does this mean I will have to make a DOS boot floppy? If so, how do I make it? What is the DOS command? ( E: \win98 ) ??? Fdisk is a program in win98? Please advise. Thanks! 

When your advice works, I'll PM you to get your addy so I could mail you a MJ or EP CD. 

Thanks again. :D

> **mister_p_1998 said:**
> I think you need a boot floppy, dont think 98 can boot from CD can it?
you'll need to run fdisk in dos to erase all non-dos partitions.
Steve

---

### Post by tomasrey88 on 2009-07-21
> **djdarrin91 said:**
> Rough spot for sure.is booting from usb an option?

No, bios is screwed up and would not let me change the boot drive. It goes to floppy, then C drive (hard drive). It will not boot from a cd nor usb flash no matter what bios boot order I chose; E,A,C or D,A,C.

---

### Post by Sylslay on 2009-07-21
Most easy option, find a freind with win98 and make bootable flopy :-)

OR:
Dowlnload Hiren's Boot Cd,from net, find link on google.

[http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)


Download and make bootable usb falsh memory with:

[http://www.softpedia.com/progDownload/UNetbootin-Download-108876.html](http://www.softpedia.com/progDownload/UNetbootin-Download-108876.html).

.
Load recovery softwere from usb stick and run setup na cd with win98

---

### Post by mister_p_1998 on 2009-07-22
When installing from a boot floppy. you need a dos boot disk with the drivers to access your cd drive. you boot on this floppy then change to your CD drive (probably D: then run setup on the CD, this will then install 98. Be aware, theres no updates for 98, so your running a very old OS, Internet doesnt run out of the box either if I recall. Have fun!
Steve

---

### Post by mister_p_1998 on 2009-07-22
> **tomasrey88 said:**
> No, bios is screwed up and would not let me change the boot drive. It goes to floppy, then C drive (hard drive). It will not boot from a cd nor usb flash no matter what bios boot order I chose; E,A,C or D,A,C.

You need a new battery in your motherboard, only a few pence.
Steve

---

### Post by tomasrey88 on 2009-07-24
mister_p_1998 and Syslay are both right. I need a DOS boot disk and Hiram's boot disk is just a fancy DOS boot disk. The problem is that the driver on the DOS boot disk will not run my CD ROM. It runs out of the driver in windows, but windows is gone. I also did not want to install from the 100 floppies that it will take to replace the CD ROM windows installer, but I got an idea. The CD ROM works fine with Ubuntu Linux, so I copied the CD ROM onto the hard drive into the formatted (& deleted :-(  ) windows partition. Then, I rebooted with the DOS boot disk and told it to install from the hard drive. Then, I reinstalled Ubuntu Linux to recompile the Grub with Windows startup option in the start menu. Yay! 

Sheesh! The last time I used DOS commands was almost 30 years ago!!!

mister_p_1998 and Syslay, I owe you a MJ CD, EP CD, or some help with your Rife project. Take your pick and PM me! I will mail the CD to you free of charge. Thanks again!

:-)  :-)  :-)

---


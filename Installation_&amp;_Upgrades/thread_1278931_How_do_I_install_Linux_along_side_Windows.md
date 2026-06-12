---
title: "How do I install Linux along side Windows"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by Rick Abraham on 2009-09-30
Hi guys I am running Ubuntu on my laptop and am loving it.
I also have a desktop PC which I am using with Windows XP, I have to keep Win XP for some particular software I using. But I would love to put Linux on that also.
This PC has a 160GB HD which Windows is on but I have a spare 120GB HD which I was thinking of installing Ubuntu on.
Ive never set up a system with dual operating systems on it and being a Linux newbie could I please have some advice on the best way about going about this.

Are there any good tutorials with a step by step guide so I dont stuff anything up.
Any help would be great.

---

### Post by overdrank on 2009-09-30
> **Rick Abraham said:**
> Hi guys I am running Ubuntu on my laptop and am loving it.
I also have a desktop PC which I am using with Windows XP, I have to keep Win XP for some particular software I using. But I would love to put Linux on that also.
This PC has a 160GB HD which Windows is on but I have a spare 120GB HD which I was thinking of installing Ubuntu on.
Ive never set up a system with dual operating systems on it and being a Linux newbie could I please have some advice on the best way about going about this.

Are there any good tutorials with a step by step guide so I dont stuff anything up.
Any help would be great.
Hi and the [GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall") should help. :)

---

### Post by pmlxuser on 2009-09-30
try these .. links


[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

you can also just goolge the same

---

### Post by raymondh on 2009-09-30
Hi and welcome.

As mentioned above (and to add a little)

1.  Back-up your files
2.  Try a liveCd session in the desktop first (to see how it plays with your system)
3.  When ready .... in step 4 (partitioning stage), make sure the 2nd HD is selected, where you plan to install Ubuntu
4.  In step 7, choose advanced (bottom right) and install GRUB in the MBR of the 1st HD, where the windows bootloader is. GRUB will overwrite that and be your bootloader from then on ... giving you the option which OS to boot on start-up. 

*If not (and you install GRUB in the MBR of the 2nd HD), you will have to manipulate BIOS on start up to boot-first the appropriate HD which contains the OS you wish to use.  This is because you now have 2 separate bootloaders in their respective MBR.

[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

Above-link has some good read to research on prior to moving on/installing.

Good luck.

---


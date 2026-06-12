---
title: "Dual boot with windows xp, two hard disks?"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by searchfgold6789 on 2009-10-12
Hi, classic help issue. I had windows xp on one 30GB hard disk (slave), but I copied that partition to another 120GB hard disk (master) and deleted the original partition. It now says operating system not found upon boot. From here, how do I create a dual boot system, with Windows on the 120GB drive and Ubuntu 9.04 on the other 30GB disk, hassle- and risk-free?
Thanks,
 - Richie
:confused:

---

### Post by PrePenguin on 2009-10-12
Did you make sure you set the new HD as your boot Drive in the bios?

---

### Post by searchfgold6789 on 2009-10-12
yes. But when I first changed my BIOS around, it looked like the BIOS was starting to open a blue window-thing, but no words appear... that stopped after about 3 reboots and 4 changes of BIOS.

---

### Post by searchfgold6789 on 2009-10-12
Now attempting to install Ubuntu on the 30GB disk, selecting option: Use the Entire Disk. Crossing fingers.... STOP ME!!! :)

---

### Post by searchfgold6789 on 2009-10-12
Actually, you do not need to stop me, because the Installer stopped me. It said:

/yah-dee-dah-dee-dah/:no such file or directory. Burn disk at lower speed, clean disk, clean drive. Quit, exit, or stop? :P

I will try to burn another disk, md5summing it this time.

---

### Post by raymondh on 2009-10-12
> **searchfgold6789 said:**
> Now attempting to install Ubuntu on the 30GB disk, selecting option: Use the Entire Disk. Crossing fingers.... STOP ME!!! :)

If the 120GB is the first to boot in BIOS .... and you prefer not to be changing BIOS boot-order every time you select an OS ... I suggest you install GRUB in the 120GB (which can be done in step 7 by clicking 'advanced').

You can also install GRUB in the mbr OF THE 30gb.  Like I mentioned .. you just have to change which HD boots first whenever choosing an OS to work on.

Back-up too.

---

### Post by searchfgold6789 on 2009-10-12
what?

---

### Post by searchfgold6789 on 2009-10-12
And can someone tell me how to md5sum the iso file for 9.04, but in plain english? the instructions on the website make no sense to me...

---

### Post by oldfred on 2009-10-12
Nothing in life is hassle and risk free.:) Make sure you have back ups.

I think Raymond is saying that you can put Grub in either or both MBR's and depending on which drive you set in BIOS to boot first will use that MBR. 

Also depending on how you copied the Partition you may not have all the windows boot info that is in the boot sector of the windows partition. You may have to run the XP recovery console and do the fixboot c: (and maybe fixMBR, if you want windows in that drives MBR) to make it right. Did you check to see if it booted?

---

### Post by searchfgold6789 on 2009-10-12
what is an MBR? 
Darn, I should probably know this stuff!

---

### Post by searchfgold6789 on 2009-10-12
and how do I get grub on the disks?

---

### Post by PrePenguin on 2009-10-12
> **searchfgold6789 said:**
> what is an MBR? 
Darn, I should probably know this stuff!
 
Master Boot Record and grub is already on the ubuntu disk try a re-install and use the grub bootloader when asked..

---

### Post by searchfgold6789 on 2009-10-12
Ubuntu is not installed on my computer. I am booting from the Live CD.

---

### Post by raymondh on 2009-10-12
> **searchfgold6789 said:**
> Ubuntu is not installed on my computer. I am booting from the Live CD.

Assuming windows is booting OK ....

You are going to install Ubuntu in the 30GB HD.  If I am not mistaken, your computer is set to boot first the first HD (this is a BIOS selection that you can change).  Since you are installing Ubuntu in the second HD, you won't be able to access Ubuntu unless

-  You change the boot order in BIOS so that the 2nd HD is first to boot or,
-  You install GRUB in the Master Boot Record (MBR) of the 120GB HD ... which coincidently is the HD that is set to boot first.

What do you want to do when it's time to select an operating system?  Do you want to keep on changing BIOS boot order (depending on which OS you want to use)?  If yes, then forget about 'advanced" as GRUB will install in the MBR of the 30GB HD. 

Do you want to keep BIOS as it is but still have the option to select an OS whenever you start your computer?  Like I said previously (during the install of ubuntu) in step 7 .... select 'advanced' and install GRUB in the MBR of the 1st HD.

Here's a reference read for you.

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Re: MD5

I have not done that for quite some time as I have chosen always to download from a torrent site which automatically checks the MD5.

If windows is not booting OK, you want to fix that first before installing Ubuntu?

Regards,

---

### Post by searchfgold6789 on 2009-10-13
Windows is currently a copy of itself; patched a bit with the Recovery Console. I want tell BIOS to boot from the 120GB, installing GRUB on that disk. HOW DO I INSTALL IT? :confused::confused::confused::confused::confused::confused::confused::confused: Oh now I get it... but the install fails. I will fix that...

---

### Post by searchfgold6789 on 2009-10-13
Just ignore the 30GB one for now.

---

### Post by raymondh on 2009-10-13
> **searchfgold6789 said:**
> Windows is currently a copy of itself; patched a bit with the Recovery Console. I want tell BIOS to boot from the 120GB, installing GRUB on that disk. HOW DO I INSTALL IT? :confused::confused::confused::confused::confused::confused::confused::confused: Oh now I get it... but the install fails. I will fix that...

One sure way to "*ignore the 30GB*" and to "*install GRUB in the 120GB*" is to physically detach the 30GB.  That way, you are assured that ubuntu will install in the 120GB and, GRUB will also install in the MBR of the 120GB.

Another way (if you don't want to detach the 30GB) is to highlight the partition that you want to install Ubuntu (the 120GB) and then finish the install process with it.

Once done. You need to ensure that BIOS will boot the 120GB **FIRST** .... before the CD drive, before anything else (just in case you hook up the 30GB again).

Regards,

---


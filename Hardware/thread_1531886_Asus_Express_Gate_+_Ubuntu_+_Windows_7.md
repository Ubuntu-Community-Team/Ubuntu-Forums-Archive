---
title: "Asus Express Gate + Ubuntu + Windows 7"
date: 2010-07-15
forum: Hardware
---

### Post by townsfolk on 2010-07-15
Hello,
   I recently purchased an ASUS UL30A-X5K for my wife. I was going to dual boot it with Windows 7, and Ubuntu (10.4), but she got really used to Express Gate being available via the Express Gate power button.

I would still like to install Ubuntu so that I can use the laptop when I need to, but I want Express Gate to continue working as is.

I did some searches and found some folks trying to replace Express Gate with Ubuntu, and I found another post where Ubuntu had wiped the Express Gate out (1).

I found a launchpad bug about Grub2, which made it seem that what I want is completely possible (2).

Has anyone had any success dual (or triple) booting one of these mini laptops so that the Express Gate button still works with Express Gate, but the regular power button provides a grub boot screen to choose between Ubuntu and Windows?

Any help or advice would be greatly appreciated.

Thanks,
Eric

(1) [http://vip.asus.com/forum/view.aspx?id=20100504225333187&board_id=20&model=Eee+PC+1005PE&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20100504225333187&board_id=20&model=Eee+PC+1005PE&page=1&SLanguage=en-us)
(2) [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/581028](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/581028)

---

### Post by townsfolk on 2010-07-19
For me, I didn't need a large harddrive partition so the in Windows installer (wubi) worked fine for me. The 30 gig limit was enough for normal development, and didn't affect any of the partitions.

---

### Post by Roman0 on 2010-11-27
*bump*

I also would like to know if this can be done. What I want is a working ExpressGate button, that runs the ExpressGate "distro", and the normal PowerOn button that would simply run the grub selection menu from where I would be able to select the other two systems (Ubuntu and Windows). I googled for it, and didn't find if anyone did manage to do something similar.

---

### Post by fermilesi on 2011-01-19
> **Roman0 said:**
>  I also would like to know if this can be done. What I want is a working ExpressGate button, that runs the ExpressGate "distro", and the normal PowerOn button that would simply run the grub selection menu from where I would be able to select the other two systems (Ubuntu and Windows). I googled for it, and didn't find if anyone did manage to do something similar.
 
Same for me. Also want to install Ubuntu (Win7 64 bits already installed in new notebook) trying not to remove Express Gate Cloud. Or, if Express Gate must be lost, (maybe better?) to use the Express Gate key to boot into Ubuntu directly!!!
 
Anyone? Would posting the actual MBR contents be of any help?

---

### Post by fermilesi on 2011-01-21
Just plunged into installing 10.10 decided to lose ExpressGate if required.
 
Dual-boot (Ubuntu+Win7} working fine, and Express Gate still there! [Asus X5MJF/N53JF]
 
Great!
 
[now fighting with audio and video drivers... but that's a different thread ;) ]

---

### Post by mathew7 on 2011-02-16
I bought an Asus T101MT and changed it's HDD with an SSD (mostly for shock reliability, but also for performance).
So  I copied over the windows partition. For the recovery partition I  wanted to check what is required, so I only copied the relevant stuff  (and recovery was working). So next step: ExpressGate.
I saw that it  has a small partition (21MB) with type 0xEF (EFI boot?). I dd-ed it and  it would not work (EG button and power button did the same thing). So I  checked the original recovery partition and saw a folder (EG or  something derived from ExpressGate) and copying it (around 230MB) would  make it work, just like before.
So my BIOS loads the partition with  0xEF, which checks the recovery partition (probably by it's ID) for  specific files/folders and loads them. If the files are not found, it  will issue a soft reset, at least in my case. When it was not working, I  got the whole BIOS initialization screens, but when it worked, nothing  was displayed from BIOS, just the EG boot.

My next steps are to wipe the SSD and restart using GPT partitions, with EG as the main test.

---

### Post by srs5694 on 2011-02-16
Type 0xEF is the Master Boot Record (MBR) code for an EFI System Partition (ESP; see the [Wikipedia page](http://en.wikipedia.org/wiki/EFI_System_partition) for details). This is used in the boot process on EFI-based computers. Most such systems use the GUID Partition Table (GPT) rather than MBR for partitioning, but EFI does permit booting from MBR disks. If the computer uses EFI, then it's not really a BIOS. This alters the way the computer boots, but doing a dd copy of the ESP, along with the OS partition(s), *should* enable the computer to boot. I can't say why it's not working for you, though; I just wanted to chime in with a bit of background information.

---

### Post by smauleon on 2011-06-15
I recently bought an Asus X35S with W7 and a fine selection of bloatware. It's a drama that a new laptop takes nearly two minutes to boot!

Today I resized the DATA partition and installed Ubuntu 11.04 there. Express Gate has not been affected, it boots instantly when I use the left side start button. And by the way, Ubuntu does in 20 seconds...

---


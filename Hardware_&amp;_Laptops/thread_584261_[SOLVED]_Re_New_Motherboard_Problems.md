---
title: "[SOLVED] Re: New Motherboard Problems"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by BatPenguin on 2007-10-20
> **RicJD said:**
> Hi ukripper

it all went ok.  I have to load in some extra modules for the jmicron sata to ide chipset otherwise it will only boot ever 20 times or something.  also i h  to install 64bit to get ubuntu to see all my memory.  and then stupidly last night, after everything was up and running for a few days i went to repartition my external harddrive using fdisk and picked the wrong harddrive (i got my internal).  so a full reinstall (home dir and all) is needed anyway :(  but at least i know i can get everything working easily

Hey there,

I just got this motherboard and I'm having MAJOR difficulties getting anything working. It just freezes on Live CD bootups etc...could you please let me know how you installed Ubuntu on this board? Alternate CD? Thanks

Mod Note: [Post being referred to]("http://ubuntuforums.org/showthread.php?t=480255").

---

### Post by BatPenguin on 2007-10-22
I'm replying to my own post in case somebody for looking information about this motherboard. I solved my problems. 

The motherboard that was giving me problems was Abit AB9 GuadQT . It wouldn't install anything, Ubuntu Live CD would hang and Windows XP installation CD would just randomly reboot. I solved this by updating to the newest BIOS (from August 2007). After this, Windows installed but Ubuntu would hang on bootup unless I added "irqpoll" to the grub boot options. After that, everything seems to work fine. Well, apparently only  3 GB of my 6 GB is recognized, I'll have to look into this. Edit: Well, this is apparently a limitation of ALL 32-bit OS's. So my bad for buying too much memory =)

Please contact me if you have problems installing with this board, I'll be happy to tell you in more detail what I did.

---


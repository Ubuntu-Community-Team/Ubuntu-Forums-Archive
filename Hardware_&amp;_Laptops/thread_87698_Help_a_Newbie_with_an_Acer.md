---
title: "Help a Newbie with an Acer"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by Madlec on 2005-11-08
Hi all. I have been reccomended Ubuntu by a friend at work, so I installed it on my old HP Omnibook with no problems at all, and I must add, it looks and feels good. :D  I now want to install it on my new laptop (purchaced before I downloaded Ubuntu, otherwise I would have got an IBM), which is an Acer TravelMate 4151LMi. The CD boots fine, and I can start the installation. But when it tries to detect the hardware, it can't find the CD drive, and then obviously fails. Being a complete novice I dont even know if it is the IDE which is undetected or the CD drive. The laptop is running an Intel 915 chipset and the CD drive is a "Slimtype DVDRW SOSW-833S" according to the Windows XP device manager. Can any one help?? I came so close to getting to grips with Ubuntu.. :cry:

---

### Post by neels on 2005-11-08
My "Acer TravelMate 210 Series" stopped at boot while detecting the "ide-cd". It booted fine when I said pci=noacpi (appears in one of the F3..8 help pages upon cd boot).
noapic nolapic did not do it for me.

I also specified "framebuffer=false", seemingly without effect. But it booted Breezy i386 from install CD -- finally.

---

### Post by neels on 2005-11-08
that is
boot: linux pci=acpi

---

### Post by Madlec on 2005-11-09
I tried that with no effect.... :(  Forgive me for being stupid, but does Kubunu run on the same kernel?:confused:  or I might give that a try.

---

### Post by Madlec on 2005-11-28
Im still tyring. I have now tried a USB CD drive which gets me further.... until it fails to find my hard drive :(  My Acer has the same chipset and IDE controller as my friends IBM and that works a treat, even more confusing.... 
  Has any one got any ideas??? I have also tried 5.04 but that had the same issues.

---

### Post by phate on 2005-12-10
I have an Acer 4150LCi, and I have the same problem "No common cd-rom drive detected".  I have tried both Ubuntu 5.04 and 5.10, but with no luck.  I have also tried both the livecd versions and the install versions of the cd's.  Same result.

I have tried all the following combinations of boot parameters:

live noapic
live noapic nolapic
live acpi=off noacpi
live pci=acpi
live pci=noacpi

but none of them will let my dvd/cd-rw drive be detected.  I have searched far and wide for a solution to this problem.  It seems to be a problem only with Ubuntu, and no other Linux distro.  I can boot fine off of countless different livecd's (knoppix, etc...), and I am able to install MEPIS and Slackware no problem.

I am not aware of a solution to this issue, and if anyone has any other ideas about possible fixes, I'm sure us Acer-415x laptop users would much appreciate it...

---

### Post by er-ku on 2005-12-11
Try the "irqpoll" option suggested in [this thread](http://ubuntuforums.org/showthread.php?t=75002):

boot: linux irqpoll
or
boot: live irqpoll

---


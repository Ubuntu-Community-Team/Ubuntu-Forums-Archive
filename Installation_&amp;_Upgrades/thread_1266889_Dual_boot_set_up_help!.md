---
title: "Dual boot set up help!"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by sale666 on 2009-09-15
Hello i need some help setting up my PC.. ok i want to dualboot (was dualbooting but with wubi, i reinstalled windows and will reinstall linux all new..) vista x64 because i need itunes and call of duty 4 and ubuntu for the rest! i have 2 HDD's
1. 500GB 2. 200GB

I have installed vista on the 500GB one and the thing is the other drive is there as drive D: but now if i install ubuntu on the drive D: vista will not boot! i know it as a fact because it stores the files on the drive D:! How could i make it store files to drive C: so i can use the entire HDD for ubuntu?

Thanks 
Sasha

---

### Post by Bartender on 2009-09-15
20+ people have looked at this thread and moved on.  My guess is because it's too hard to understand what you're saying.
How do you know vista won't boot with Ubuntu installed to the second drive?  Did you try it?  If so, we would need to know what the error was - a grub error, blank screen, BSOD, what have you.  And if you did try it already, how did you fix the problem?

I don't know what you mean by "storing the files on C" because you say you want Ubuntu on "D".  It would be better to use Linux lingo for devices.  Your first HDD is probly recognized as sda and your second HDD is probly recognized as sdb.

I have one suggestion that you could try that might at least give us a starting point to discuss.  Turn off the PC and unplug the power cord.  Unplug sda (the Windows HDD) from the system.  You don't have to disconnect power and data cables, one or the other will do it.  I usually pull both but that's just me.  With only the 200GB HDD plugged in, plug the power cord back in, start the PC, and try to pop the Ubuntu install CD into the optical tray really quick or get it in there and restart the PC again.  Install Ubuntu.  The installer will only see one HDD, so all of the Ubuntu files will go to that drive, including the tiny blip of data that might go the Windows MBR in a standard dual-boot.

Does Ubuntu work?  If so, unplug the PC from the AC voltage again, and plug the WIndows HDD back in.  You might have to check settings in BIOS, but the PC "should" boot to the Windows HDD.  

Does Windows work?  

If so, either go into BIOS and change boot device priority to the second HDD, or use the appropriate keyboard button while restarting the PC to choose the second HDD from the boot option that's built into most if not all modern BIOS'es.  See if it'll boot to Ubuntu.

Report back with your findings please.

---

### Post by presence1960 on 2009-09-15
> **Bartender said:**
> 20+ people have looked at this thread and moved on.  My guess is because it's too hard to understand what you're saying.


+1

I passed this over a few times because I do not understand what the OP is trying to say.

Edit : I think I cracked the code. Vista will boot if you install Ubuntu to the 200 GB disk. Either disconnect the windows disk or when you go to install Ubuntu go into BIOS first and make the 200 GB disk first in hard drive boot order. Install Ubuntu. After Ubuntu is installed if you used the method of disconnecting the Windows disk connect it and go into BIOS and set the 200 GB disk as first hard disk to boot. This will bring up GRUB. You will have to boot into Ubuntu and add a Vista entry to menu.lst. When you boot the GRUB menu will come up and you can choose which OS to boot into. GRUB is able to boot multiple OSs. 

If you are a noob I would prefer you disconnect the windows disk, for if you install ubuntu to the wrong partition you may wipe windows.

---


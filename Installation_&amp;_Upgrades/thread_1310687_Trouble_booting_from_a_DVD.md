---
title: "Trouble booting from a DVD"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by dcook11 on 2009-11-02
I installed Ubuntu 9.10 (my first linux distro) a couple days on my old Dell Dimension 8300 from a DVD I burned with the disk image on it. That installation went fine and it still works great.

However, I wanted to check out the server version of Karmic, so I burned a DVD of the disc image and tried to boot from the DVD just to try it out. For some reason my computer will no longer boot from both the DVD with Ubuntu Server on it or the original DVD from which I installed Ubuntu Desktop.

My Process:
While the BIOS screen is loading (I'm using BIOS version A02) I press F12 to take me to the Boot Menu. From there, I tell it to boot from the IDE CD-ROM device; this worked originally, but then it started to boot straight into the version of Ubuntu that I had already installed. In the setup menu, I removed the Hard-disk from the boot sequence so that booting from the CD-ROM device was the only option, and now when I tell the Boot Device Menu to boot from the CD, a message pops up that says "Strike the F1 key to continue, F2 to run the setup utility". (This message also appears when I try to boot normally but then it's preceded by a Low Battery Voltage message, and when I press F1 the computer boots into Ubuntu) When I press F1 in the Boot Device Menu, a similar message appears that says "strike F1 to retry boot, F2 for setup utility", and when I press F1 again another message appears that says:
"No boot device available -
  strike F1 to retry boot, F2 for setup utility"

When I boot the Ubuntu that I've already installed, the DVD appears on the desktop and it has the proper contents, so the drive seems to be working. Since I installed Ubuntu, I've added a wireless card but haven't made any other hardware changes. I'm almost positive that all of the setup preferences are the same as when I installed Ubuntu successfully. 

When I select IDE Drive Diagnostics from the Boot Device Menu, the F1/F2 message comes up again and after I hit F1 it runs the drive diagnostics and returns:
"Primary SATA
          Drive 0: No device
Secondary SATA
          Drive 0: No device
Primary IDE
         Drive 0: ST3120026A - Pass
         Drive 1: No Device
Secondary IDE
         Drive 0: SAMSUNG DVD-ROM SD-616T - Diagnostics not supported
         Drive 1: _NEC DVD+RW ND-1100A - Diagnostics not supported
Test complete, Press <ENTER> to reboot"

That's all the info I can think to provide. If there is anything else that might help please let me know. I've been searching the internet and trying everything I can think of for several hours and nothing has worked. If anyone could give me some tips or advice, I would REALLY appreciate it! Thanks!

---


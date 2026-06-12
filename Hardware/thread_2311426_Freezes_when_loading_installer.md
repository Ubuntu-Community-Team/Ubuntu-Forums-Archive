---
title: "Freezes when loading installer"
date: 2016-01-27
forum: Hardware
---

### Post by Johnathan_Simpson on 2016-01-27
Ok i downloaded the iso(14.04.3 and 12.04 both 32 and 64bit) from the ubuntu site. Used Rufus, Unenbootin, and Linux live usb creator to create bootable usb(formated to fat32 4gb). booted via uefi and selected install i get a restor sound fail. so i tried nomodeset and i get to where the desktop would be but the mouse doesnt respond and nothing else pops up. the task bar goes away. and thats as far as ive gotten on installing it. any advice?

System
amd fx4350
R9 290
990fxaud5
16gb ddr3 1600mhz
Windows 10 USB installed with fresh drive so secureboot=off
UEFI and Legacy same result

---

### Post by mörgæs on 2016-01-27
Hi, welcome to the fora.
Have you tried 15.10?

---

### Post by Johnathan_Simpson on 2016-01-31
ok i found [this]("http://ubuntuforums.org/showthread.php?t=2309548") in another thread where you changed the iommu setting and it worked. got it installed via [this]("http://www.instructables.com/id/Dual-Boot-Ubuntu-and-Windows-8-UEFI/?ALLSTEPS") process. i get grub2 to and windows boots but when i select ubuntu it acts like its not there just a blank screen and my monitor turns off. the install was on sdc not sda if that matters.

---

### Post by Vladlenin5000 on 2016-01-31
No, in this case it doesn't matter where. What matters is your graphics card not being supported by the default open source driver for Nvidia cards.
You need to edit the Ubuntu entry and add *nomodeset* to the line where "quiet splash" is. Then you'll have generic low resolution video so you can install the proper drivers for your graphics card. Search "drivers" in the dash, choose "additional drivers", then select and apply the recommended one. Reboot.

---

### Post by Johnathan_Simpson on 2016-02-01
Ok that worked but now im stuck in a login loop.


UPDATE: Did a format and reinstall with only *sdc1 /* and *sdc2 swap area* and installed bootloader to *sdc*. Booted via *nomodeset *with no login issues. Thanks Vladlenin5000

---

### Post by Vladlenin5000 on 2016-02-01
I would consider the suggestion in post#2.
Newer hardware, latest release... You've been almost all over the place except where you should have been: The latest Ubuntu release (15.10) and, obviously, _64-bit always_.

Considering you just installed I see no point in troubleshooting.

---

### Post by Johnathan_Simpson on 2016-02-01
I guess i didnt respond to that one. Sorry Morgaes. I am currently trying 15.10 64-bit as advised in Post #2 but still had the problem with the install which was fixed in post #3. Probably should have mentioned that.

Ok now in nomodeset, search drivers, select additional drivers, there is an opensource driver thats already installed it looks like(install is greyed out) and 2 proprietary(fglrx, fglrx-updates). Then there is unknown:unknown which is set to not use this device and has a proprietary proprietary selection as well.

 Do i use the proprietaries?

---


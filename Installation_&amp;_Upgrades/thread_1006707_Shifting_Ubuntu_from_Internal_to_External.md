---
title: "Shifting Ubuntu from Internal to External"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by Bohlio on 2008-12-09
Currently, I have Ubuntu Fiesty on a 160G IDE hard drive. I know the steps necessary to physically make it into an external USB hard drive, but I don't know what is necessary at a hardware level in order to make it portable and bootable. Does anyone know what needs to be done in order to make an internal HD with ubuntu into a portable (multiple computers) USB bootable system?

I'm pretty sure I'm going to need to do something with GRUB and make the OS scan for new hardware every time it boots, but I don't know how to go about doing any of that. Any help would be greatly appreciated.

Thanks,
Bohlio

---

### Post by zwygart on 2008-12-09
If you booted it normally internally, GRUB is already installed.
All what you ahve to do is set the destination computers BIOS to boot from USB or external HD. For this you have to press a key on boot up (F1,F8,F9,F12,Tab,del or any other) and change the boot order.

---

### Post by Bohlio on 2008-12-09
> **zwygart said:**
> If you booted it normally internally, GRUB is already installed.
All what you ahve to do is set the destination computers BIOS to boot from USB or external HD. For this you have to press a key on boot up (F1,F8,F9,F12,Tab,del or any other) and change the boot order.


I'm no stranger to booting stuff from something other than the hard drive, so I know that, I thought that I'd have to do something to tell grub that the hard drive is no longer on the primary IDE cable but is now a USB device. 

Otherwise, If you boot from a USB drive with grub configured to boot from a hard drive, It would try to boot ubuntu from whatever hard drive is on the computer you're at. I guess what I'm looking for is some way to make grub boot from the Ubuntu partition relative to where it is located, and for a way to scan for new hardware automatically on boot-up (It may already do that, Im not sure)

Thanks
Bohlio

---

### Post by zwygart on 2008-12-10
OK, I boot often on USB flash drive. I think you know that grub calls drive like (hd0,0) and so on. Grub see internal and external drives (HD and flash drives) exactly the same way, only the numbers grow (hd3,0). So when I want to root my USB external flash drive I write (hd0,0), because the drive where GRUB is on is the first for Grub. Any way I think you can try som thing, you cannot lose anything. That's why I said you only change it. Grub is on the drive so the drive will stay first.

If you want to try temporarly some drive, at boot prompt press C. You came at a prompt where you can try commands. 
If you want to change permanently, change the specific section in /boot/grub/menu.lst

To help you Here is the Manual of GRUB
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
This should help you. If not post what happens when you plug the drive as external and boot from it.

---


---
title: "GRUB error 21 when USBHD is unplugged at startup"
date: 2008-09-15
forum: General Help
---

### Post by mjpmjp on 2008-09-15
I just installed Ubuntu 8.04.1 on a USBHD with WindowsXP on the internal HD (C:drive). If I unplug the USBHD before turning on the laptop or restarting it, WindowsXP does not start automatically and I get a GRUB error 21. I would like to modify GRUB so that WindowsXP starts up normally if the USBHD with Ubuntu installed on it is not plugged into a USB port. I guess a file on my C: drive where WindowsXP resides was modified also?

---

### Post by issih on 2008-09-15
Your problem is that grub itself was installed onto the mbr of your windows hard drive. The error shows up because grub is expecting to find 2 operating systems, but because you have unplugged the usb drive it can't find one and errors out.

Solutions...
To get windows back...se either an xp install cd or super grub disk to restore the windows boot loader to the mbr of the windows drive.

Then you need to install grub onto the mbr of the usb drive..
This can be done in a few ways, but the easiest provided you have little wirth saving on your ubuntu install is to reinstall ubuntu onto the drive, but this time at the last step before installation hit the advanced button and tell ubuntu to install grub to the usb drive not the internal one.

Once that is done you can select which os you want by choosing which device to boot from (modern bioses typically offer a list accessible from a hotkey) or alter the boot order in the bios to try th usb drive first, so that ubuntu is booted if the drive is there, but otherwise windows does.

Hope that helps

---

### Post by mjpmjp on 2008-09-15
> **issih said:**
> Your problem is that grub itself was installed onto the mbr of your windows hard drive. The error shows up because grub is expecting to find 2 operating systems, but because you have unplugged the usb drive it can't find one and errors out.

Solutions...
To get windows back...se either an xp install cd or super grub disk to restore the windows boot loader to the mbr of the windows drive.

Then you need to install grub onto the mbr of the usb drive..
This can be done in a few ways, but the easiest provided you have little wirth saving on your ubuntu install is to reinstall ubuntu onto the drive, but this time at the last step before installation hit the advanced button and tell ubuntu to install grub to the usb drive not the internal one.

Once that is done you can select which os you want by choosing which device to boot from (modern bioses typically offer a list accessible from a hotkey) or alter the boot order in the bios to try th usb drive first, so that ubuntu is booted if the drive is there, but otherwise windows does.

Hope that helps

_[COLOR="Blue"]**Thank you again, issih!!! Used super grub to restore WindowsXP to boot as you suggested......mjpmjp**[/COLOR]_

---

### Post by issih on 2008-09-15
You're welcome :)

---


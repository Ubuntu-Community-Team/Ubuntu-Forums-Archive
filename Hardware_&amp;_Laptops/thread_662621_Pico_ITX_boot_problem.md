---
title: "Pico ITX boot problem"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by Nzer24 on 2008-01-09
I just bought a new Via PX10000. I know it's not very mature, but it just looks so cool.

So, I have a boot problem. I am unable to attach a CD drive because I don't have a SATA or USB one, so I installed Xubuntu on a laptop hard drive using an IDE-IDE adapter and my desktop computer. I am able to boot GRUB and all the installations from that drive, and they work perfectly.

However, when I attach it to  the PX, the startup gets stuck on "Verifying DMI Pool Data". I know this means there is something wrong with the boot device, but I can't figure out what. I was, however, able to boot Windows 98 on a different drive without any problem. 

I know there is no problem with the BIOS, nor with the hard drive. I assume it is the bootloader. Have there been problems with Award BIOS and GRUB? Would LILO help? I am planning to only use Xubuntu and Gentoo on the computer, so that shouldn't be a problem.

Also, I have heard that not drawing enough power from a PSU can make the voltage unstable. I know that I am only drawing about 15W max from a 450W PSU, so if that is true it could be the problem.

Any ideas?

My specs and other devices used for testing: (Just in case it helps...)

Via PX10000 with Award BIOS
1 GHz Via C7 nano-BGA low voltage processor
1 GB 533MHz DDR2 SODIMM
80GB Fujitsu 4500 RPM 2.5" hard drive
450W DiabloTek PSU (leftover from desktop build)
4GB flash drive
ZyXEL USB wireless card compatible w/ zd1211
PS/2 keyboard + mouse
High speed wired internet connection

---

### Post by Nzer24 on 2008-01-09
Well, I got some stuff to work. I set it up so the IDE is now connected to a CD drive. I don't have the hard drive in becuse of this, but I was able to boot from a Xubuntu live cd. I am now actually using the device to post this and attempting to install Xubuntu on a flash drive. 

This leads me to believe that the PSU is not the problem.

Any ideas?

---

### Post by Nzer24 on 2008-01-10
Fine, if the PX10000 is scaring everyone away, just imagine that it's a problem between Award BIOS and GRUB.

What would cause this? I'm sure someone knows.

---

### Post by XorXaX on 2008-01-11
Hello!

Did you ever get Ubuntu to run och Via Pico-ITX?

Thanks!

Sincerley,
Jonas

---

### Post by justhamade on 2008-02-06
Dude, you can't install it on different hardware and then expect it to work.  The CPU is different, the Chipset is different, im sure an x86 (i386) kernel will work but good luck trying to install it that way.

Install options would be:
Net boot (pxe) if the pico supports it, this i how i install debian on soekris devices
USB cdrom drive, or other usb device.

You could also try to boot into recovery mode and fix what ever modules are problems but that would take forever.

---


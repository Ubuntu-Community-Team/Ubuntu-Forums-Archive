---
title: "2 gfx (amd + nvidia) install on 14.04 ubuntu 64bit boots to unknown opcode crash"
date: 2014-04-24
forum: Hardware
---

### Post by nedrerairo on 2014-04-24
Hi!

nouveau E (Vbios) (device#:device#) ... unknown opcode 0x01
nouveau E (devinit) (dev#...same as the above)  init failed, -22
nouveau E (drm)  failed to create 0x80000080, -22

is the system message given when it refuses to load anymore.  I had it installed fresh, booted once today and loaded fine, then updated via update manager and after reboot .. well this.

as far as I can tell it is due to me having 2 gfx cards and some driver is steering the show and refusing to recognise my other card and panicking .. anyone else have a theory?

suggestions to how to fix it?  No problem to reinstall, just pondering if I should just drop installing 14.04 and wait for 14.10 when devs get their stuff right...

cards in use are a) AMD 6850 radeon and b) a gtx 670 Nvidia card..  both installed on a Asus crosshair formula IV (890fx chipset) motherboard..

I'm trying to get this system usable for kvm with pci passthrough (gaming + base system), but this is occurring even before I get started :( ....

halp plox! :)

---

### Post by nedrerairo on 2014-04-25
Ok, so after letting it rest for a day.  It seems it was the nouveau driver loaded for nvidia card which messed up booting. 

Went to recovery via grub menu (hold shiftkey at boot), set gfx to recovery and booted up into ubuntu again.  This time I set the driver for gtx card to proprietary nvidia driver, instead of the supposedly open nouveau, which after rebooting worked fine.


so case closed.. but still a step that sucks to do with a new install

---


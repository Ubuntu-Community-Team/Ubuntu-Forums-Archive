---
title: "Booting Ubuntu from USB external hard drive - general questions"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by penguinsfly1 on 2009-09-20
Hi, I have a couple of questions about installing Ubuntu to an external hard drive:
1) Does it work very well? Are there any noticeable problems?
2) Would I be able to load it from and computer with the ability to boot from USB?
3) Does anyone know if an asus p5kpl 1600 supports booting from usb?
The reason I'd like to install to an external hard drive is that I don't really want to partition my hard drive. Thanks for any help.

---

### Post by earthpigg on 2009-09-20
> **penguinsfly1 said:**
> Hi, I have a couple of questions about installing Ubuntu to an external hard drive:
1) Does it work very well? Are there any noticeable problems?
2) Would I be able to load it from and computer with the ability to boot from USB?
3) Does anyone know if an asus p5kpl 1600 supports booting from usb?
The reason I'd like to install to an external hard drive is that I don't really want to partition my hard drive. Thanks for any help.

1 - data travels over USB cables slower than on the internal cables that connect your motherboard to hard drive. so, it will be a bit sluggish. but certainly still usable.

2 - if you install it via ubuntu's "USB Startup Disk Creator" tool, yes. if not, then no.

3 - dunno.

i suggest you use ubuntu's "USB Startup Disk Creator" tool. it comes with 9.04. you can use it from the LiveCD.

if you install it via another method, be very careful... Ubuntu has been known to ninja-attack the MBR of internal hard drives even when the user installs Ubuntu on an external hard drive.

USB Startup Disk Creator is the way to go for what you want to accomplish, and will prevent ninja attacks.

boot a LiveCD, and instead of clicking 'install' go to system -> administration -> USB Startup Disk Creator -> point it to the .iso of the LiveCD you just booted.... it will use that as its source to create a LiveUSB - similar to a LiveCD, except that you can save documents, settings, music, etc, to.

---

### Post by penguinsfly1 on 2009-09-20
Thanks for the info. I assume firewire would be faster? Would that work in the same way as booting from USB?

---

### Post by earthpigg on 2009-09-21
> **penguinsfly1 said:**
> Thanks for the info. I assume firewire would be faster? Would that work in the same way as booting from USB?

enter your bios setup and see if the option to boot from firewire is presented to you. that will answer your question definitively.

---


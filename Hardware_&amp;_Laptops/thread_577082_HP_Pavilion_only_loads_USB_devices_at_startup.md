---
title: "HP Pavilion only loads USB devices at startup"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by mrmeyers99 on 2007-10-15
Hi, I recently installed Gutsy on my HP Pavilion DV6119us and my USB devices (thumb drive, printer, wireless keyboard...) only work if they're connected when I boot my computer.  If I try to plug a USB device when it's already booted up it doesn't recognize them.  Any help please?

---

### Post by danimall on 2008-06-16
Hey I've got the exact same problem.  It's been a problem for me for the past year.  I've got an HP Pavillion dv6000 laptop and for some reason it will only mount USB devices if they are connected during startup.  When I plug in the flash drive after startup the light on the flash drive lights up briefly and then turns off like it is not even being recognized by the system.  /dev does not show any usb devices in there and fstab shows no sign of any usb devices.  It was like this on Feisty, Gutsy, Hardy, Fedora 7, and Knoppix 5.1.1, so it's not distro specific. It sounds like it has to be something to do with the hardware not being recognized by the kernel.  Another thing I would like to add is that it does the same thing with my SD card reader and my headphone jack.  If anyone has any answers or could at least point me in the right direction, it would be most appreciated.  This is the final issue I need worked out before I can finally make my Microsoft-less migration.

---

### Post by mrmeyers99 on 2008-06-16
Hey, I added noapic nolapic to the boot options, and that seemed to fix the problem.  Before I just added noapic, and supposedly you're supposed to use both.

---

### Post by danimall on 2008-06-16
My god it worked.  That just finished a year long quest of mine.  I knew about noapic and lapci=off, but I didn't know about nolapic.  Everything works perfect now.  Thanks

---


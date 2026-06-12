---
title: "UNetBootin destroying USB drives"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by N00b-un-2 on 2009-09-27
I've tried using UNetBootin to create bootable USB sticks for various distros including several linuxes and BSDs and have yet to succeed in making a flash drive that is capable of being booted from.  The only thing I've succeeded in doing is corrupting several USB sticks.  Once you use UNetBootin is there any way to safely remove the .iso boot image from it or is it like using a CD-R?

---

### Post by pastalavista on 2009-09-27
I've never had any trouble with Unetbootin. I've used it to make lots of different distros boot from USB. When I remove a distro, I usually reformat it with Gparted and start with a fresh format. All my flash drives sill work just fine.

---

### Post by bumanie on 2009-09-27
usb drives are flash memory that can be over-written many times. Try gparted to format the usb drive with and put a new filesystem on. You may even have luck with unetbootin if the drive is formated with a new filesystem. It could be the fileystem you have on there at present has errors, a format etc. will ensure that will not be an issue.

---

### Post by ddrichardson on 2009-09-27
You don't mention if you've used different types of drives, I have a Buffalo USB Stick which will not boot but appears to have been written correctly.

---


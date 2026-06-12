---
title: "USB Key Single Boot"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by stevenmitnick on 2008-01-10
When I install a new version of Ubuntu onto a USB key and Grub begins to load it becomes the boot software for Ubuntu and any other OS it finds (multibooter).

For me that means Grub overrides and becomes Vista's boot software on the hard drive. This is a problem because unless the USB key is installed, Vista won't boot up.

The next time I install a new version of Ubuntu into my USB key, I want Grub to only install into the USB key to boot Ubuntu, and not look for and alter Vista's boot software.

My goal is: 1) to be able to stick the USB key into any computer and boot Ubuntu from it, and 2) not corrupt the Vista boot software on the computer while I'm using it to install Ubuntu onto the USB key. Thus, I'm able to continue to boot Vista as I had before I installed Grub. 

Is there a way in which this can be done?

Thanks, Steven

---

### Post by EXCiD3 on 2008-01-10
Change the location of where Grub is installed to. Make it install to the MBR of the flash drive instead of the local hard drive. Grub will still automatically detect and add the entries for Windows that is detected however you can simply edit these entries out of /boot/grub/menu.lst

---


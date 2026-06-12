---
title: "Flash drive options"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by m005k on 2009-03-05
I have a couple of questions. I want to put 8.10 on a 4 gig flash drive so it behaves like a live CD. I assume this is different than just installing to the flash drive. Also, I have a laptop that doesn't boot from flash even though it is listed in the bios. Can I trick it somehow into booting from it when I want it to?

Mike

---

### Post by Rallg on 2009-03-05
1. You can put live Ubuntu on a flash (USB) pendrive. If you already have a running installation of Ubuntu, and a copy of the *.iso file that you used for installation, then look in the Ubuntu menu under System > Administration > create a USB startup disk. 1Gb suffices.

2. If you do not already have a working Ubuntu installation, but have Windows, find "Unetbootin" on the Internet, and also download the *.iso that you will need for ubuntu.

3. Just because you think a USB should be bootable, does not mean that it really is. There are tricks to making a USB bootable, no matter what your BIOS says. But if you follow 1 or 2, above, your problem is solved.

4. If you have a USB pendrive that really is bootable, but your BIOS doesn't like it, there is another possibility: You may be able to install the GRUB bootloader on the hard drive, then alter its menu.lst file so that it transfers control to the USB. Don't do this unless 1 and 2 fail, since it involves altering your hard drive's master boot record, and maybe that is not what you want to do.

---

### Post by bubwitmaingay on 2009-03-06
While the machine is loading for memory test, hit ESC key (especially if your laptop's BIOS setup can be accessed by hitting F2). In most laptop it works that way. When you hit ESC, it will pop a window with selection where you wanted to boot. Use the arrow keys to choose boot device, then enter.

Hope that helps. 8)

---


---
title: "Grub 22"
date: 2008-08-29
forum: General Help
---

### Post by Mediciman on 2008-08-29
Fixed thanks everyone.

---

### Post by Crafty Kisses on 2008-08-29
Try recovering with SuperGRUB > [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Mediciman on 2008-08-29
> **Codename said:**
> Try recovering with SuperGRUB > [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Any Idea how to use it on a USB on Windows?

---

### Post by babounours on 2008-08-29
burn another UBUNTU disk on CD-R not CD-RW.
Your computer doesn't boot because you delete the partition where grub config file was.
Reboot with a linux disk and reinstall ubuntu.

---

### Post by falcon61102 on 2008-08-29
For USB on Windows:
Once you download the verison for the USB on Windows.  You can find it at:
[www.supergrubdisk.org](www.supergrubdisk.org)

It comes with an installer that will guide you through it.  As a warning, depending on how you do the setup, it may erase all the contents of that USB drive for the install.

As far as use goes, boot up your computer from the USB drive like you would for any other USB device.  You may have to adjust a couple settings in the BIOS if you've never done that before.

---

### Post by Mediciman on 2008-08-29
> **falcon61102 said:**
> For USB on Windows:
Once you download the verison for the USB on Windows.  You can find it at:
[www.supergrubdisk.org](www.supergrubdisk.org)

It comes with an installer that will guide you through it.  As a warning, depending on how you do the setup, it may erase all the contents of that USB drive for the install.

As far as use goes, boot up your computer from the USB drive like you would for any other USB device.  You may have to adjust a couple settings in the BIOS if you've never done that before.

Mkay..So I put the Auto for Windows on my USB drive.
But, I still just Get the flashing "_" or it just says Grub error 22..Or If I make it only boot the USB it says "Operating System not found."

---

### Post by falcon61102 on 2008-08-29
You need to restore the windows MBR.  What happened is that when you deleted your Ubuntu files you deleted the files that boot your computer.  By restoring your windows MBR you can get that back.  That should be an option in Super GRUB Disk otherwise you can use a windows install disk in the recovery mode.

---

### Post by Mediciman on 2008-08-30
I still need help. My laptop won't read disc(It keeps on opening) and I would like to put it on the USB but, It just keeps flashing "_". Please I really need help.

---

### Post by babounours on 2008-08-30
change the bios options to boot on usb

---


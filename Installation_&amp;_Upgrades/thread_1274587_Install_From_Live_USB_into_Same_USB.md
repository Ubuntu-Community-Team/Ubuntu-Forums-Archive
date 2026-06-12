---
title: "Install From Live USB into Same USB"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by sanumala on 2009-09-24
Hi

Is there any way we can boot ubuntu from the live USB pen drive and install into the same drive.

I mean I have 4GB pendrive (Ubuntu 9.04 Live USB) and i want to install ubuntu into that same drive including grub and stuff.

I need instructions how to partition USB drive and make it bootable and install into the same drive's different partition like 1GB partition contains ubuntu.iso stuff and other 3GB installation.

After installing how can i make 3GB partition is active primary bootable partition.

Thanks in Advance

---

### Post by earthpigg on 2009-09-24
i don't know.

any reason you haven't just gone ahead and tried it, though?

you will be doing manual partitioning, obviously.

one thing you will want to look closely at is at the final screen before partition changes are written. you will see an 'advanced' button. click it, and point it to where you want the bootloader to go.

---

### Post by Arand on 2009-10-04
Seems like it's a tricky business currently, I tried this with Karmic and it apparently wants to umount the liveusb in the installation process, which just refuses and stops install.
- Arand

---


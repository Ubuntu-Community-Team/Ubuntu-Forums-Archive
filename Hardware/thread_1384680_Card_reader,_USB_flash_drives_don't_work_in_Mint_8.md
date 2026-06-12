---
title: "Card reader, USB flash drives don't work in Mint 8 (Karmic)"
date: 2010-01-18
forum: Hardware
---

### Post by Murrquan on 2010-01-18
Okay, this one's weird ...

I've tried out both Mint 8 and Karmic now. On the LiveCDs, they recognize my SD card reader and USB flash drive; these things automatically mount as soon as I plug them in. Once the distro's installed to my hard drive, however, neither work. (The sound also cuts out after a little while, and I have no idea why.)

What information is needed to troubleshoot this, and/or what can I do to solve it?

---

### Post by Murrquan on 2010-01-18
BUMPing this and letting you know that I've installed Karmic itself now, too. Same problem.

---

### Post by efflandt on 2010-01-19
I have not had trouble booting a regular install of 64-bit Ubuntu 9.10 from a USB hard drive (WD Passport), as long as the computer itself cooperates to boot USB.  Even though I originally installed it on a laptop where it (and grub2) were on sdb, it was able to boot the USB drive from my desktop with built-in usb memory card reader, where the drive ended up as sdf.

Although, I had problems trying to get a regular install of Mint8 on USB flash to boot from another PC.  I have not had a chance to research it much, but I think it might use devices instead of UUID and drive devices can vary on different computers.  Check what ends up in /boot/grub/grub.cfg and /etc/fstab, but changes to grub settings should be made from /etc/default/grub (and see scripts in /etc/grub.d).

---


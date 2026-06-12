---
title: "cant boot ubuntu 5.10 after installing grub on another disk"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by someuser77 on 2005-12-23
I have Windows 2000 and I installed Ubuntu 5.10 on a second HD, grub was installed on the first partition of that drive (hdb1).
I used: ```
dd if=/dev/hdb1 of=linux.bin bs=512 count=1
``` and linked it in boot.ini.
On boot, when i try to load Ubuntu from the Linux entry of boot.ini i see "GRUB" on the screen and the computer beeps, until i restart.
How can i fix grub and put it on hdb1 and link the windows loader to load it?
Do i need to force LBA32? If so, how?

---


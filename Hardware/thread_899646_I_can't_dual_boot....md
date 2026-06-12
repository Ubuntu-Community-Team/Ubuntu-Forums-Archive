---
title: "I can't dual boot..."
date: 2008-08-24
forum: Hardware
---

### Post by esrise on 2008-08-24
...I have two hard drives in my computer, one has ubuntu [30 GB] and the other has Windows XP SP2 [160 GB]. They are set to cable select and BIOS recognizes both HDD's, but won't give the option to use ubuntu or windows, it just defaults to windows. I can't access the ubuntu drive at all and i need some important papers off of it. By the way, I'm using a Dell Dimension 4550 using a Pentium 4 processor [2 GHz] and 256 MB of RAM

---

### Post by tturrisi on 2008-08-24
1. use jumpers to set the linux drive as master & xp as slave.
2. disconnect the xp drive.
3. if grub is installed on the linux drive it should boot.

The bios has no say about which op sys boots, only if a hd can boot (yes or no).

---


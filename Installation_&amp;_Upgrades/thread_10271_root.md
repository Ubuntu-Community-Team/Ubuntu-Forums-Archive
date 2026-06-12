---
title: "root"
date: 2005-01-06
forum: Installation &amp; Upgrades
---

### Post by sheine on 2005-01-06
The installation went smoothly and I chose Grub as the bootloader. I cannot edit /grub/menu.lst. I thought that it was because I was not root, but when I tried to login as root, it refused to let me do so, denying the root password that I had chosen in the installation.

---

### Post by fng on 2005-01-06
Ubuntu has root disabled by default.
try editing /grub/menu.lst with this command : sudo nano /grub/menu.lst (replace nano with your favorite editor).
If he ask for a password, just enter your own user password.

---

### Post by sheine on 2005-01-06
It worked. Thank you Ubuntu Guru.

---


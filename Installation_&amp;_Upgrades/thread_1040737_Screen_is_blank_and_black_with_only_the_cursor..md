---
title: "Screen is blank and black with only the cursor."
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by Hermanocleas on 2009-01-15
I Installed Ubuntu 8.10 on an older Gateway laptop (with no problems) and once I log in the screen goes orange then black and stays that way with just the mouse pointer visible.

---

### Post by utnubuuser on 2009-01-16
Hi -- You could try going through rescue at grub,  and in terminal do "sudo dpkg --reconfigure xserver-xorg".  or even "sudo dpkg --configure -a" to make sure everything installed properly and configured.

---


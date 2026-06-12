---
title: "Set Grub2 to install and update on boot partition only"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Jasman on 2009-11-07
Sorry if this is answered already somewhere, but my searching is coming up empty, at least with something I can understand. When I ran through the script to replace legacy grub with grub2, the only choice I'm given for where to install it is /dev/sda, which is my entire drive. I'd like to, against "recommendations," install it only to my linux boot partition and have my Win7 bootloader and EasyBCD chainload grub2. Is there a config entry I can modify for grub2 to make it install only to a particular partition and update only to the same partition? Thanks.

---


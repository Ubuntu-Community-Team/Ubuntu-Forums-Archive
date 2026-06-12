---
title: "Using the integrated graphics chip with vga_switcheroo - Ubuntu 12.04"
date: 2013-09-19
forum: Hardware
---

### Post by 34TXQ7t on 2013-09-19
Hello! I'm a complete newbie to linux. 

My laptop has two graphics chips a Radeon 4650, and the integrated Intel one.

I'm trying to set Ubuntu 12.0.4 up so that it only ever uses the integrated graphics to save power and heat. 

if I run:
$ grep -i switcheroo /boot/config-*
I get:
CONFIG_VGA_SWITCHEROO=y

However when I run:
~$ echo DIS > /sys/kernel/debug/vgaswitcheroo/switch

I get a permission denied error.

Any help would be greatly appreciated, also is there a command I can run to check which graphics card is currently in use

---


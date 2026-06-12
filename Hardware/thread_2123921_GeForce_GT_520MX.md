---
title: "GeForce GT 520MX"
date: 2013-03-09
forum: Hardware
---

### Post by peter0193 on 2013-03-09
Hi. I've got a huge problem with the drivers. I'm using ASUS X53S and I've already tried f..k knows how many ways to run my graphic card. Tried to run it at 12.10, 12.04, 64 and 32-bit, both Polish and English distributions. I have tried:
1. bumblebee - I couldn't run anything at nvidia.
2. *.run nvidia drivers from their website - stuck in 640x480px mode
3. in 64-bit 12.10 and 12.04 there were no available drivers in jockey, so i tried this: [http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html) - Didn't work, no desktop.
4. in 32-bit 12.10 and 12.04:[INDENT]a) there were no available drivers in jockey
b) there were some drivers in jockey (310, 304 and sth else). I've tried all of them. Although the instalation had completed succesfully in each case, the driver wasn't runing, so I tried ```
 X -configure 
```, then ```
 cp /root/xorg.conf.new /etc/X11/xorg.conf 
```. The result was unbootable system.[/INDENT]
5. Installing drivers from Softrware Center or Synaptic also resulted in empty desktop, even after installing headers.

I've tried even more methods, but can't remember them all. However, none of them worked, so far. Is my card completely unsupported or what?

---


---
title: "force 1080i on HDMI output"
date: 2012-01-14
forum: Hardware
---

### Post by jkransen on 2012-01-14
Hi I run Ubuntu 11.10 on my laptop, a HP G62. On the HDMI output, I connect our TV, a Philips 37PF9731. The TV supports 1080i, but not 1080p on HDMI. The native screen resolution is 1920x1080. I think I read that this line of Philips TVs incorrectly reports supported modes. I prefer to have the modes autodetected, but when I do, the best possible mode for the TV is 1024 x 768 (4 : 3), and that is not interlaced. I tried adding a /etc/xorg.conf with just one 1080i mode, but then Ubuntu boots without screen displayed. Is adding this file the right way to go, and in that case, what should be in it? The video chipset is apparently an Intel i915, as that is the driver that was loaded.

In advance I thank you for any help on this.

Jeroen Kransen

---


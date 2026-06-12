---
title: "Nvidia GeForce4 Mx  4000 driving BenQ FP231W"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by rawegg on 2009-03-22
I'm using 8.1 with the new Linux driver 96.43.11

Problem:  I can only get 1280x1024 and the system reverts to lower res on startup (the system won't let me save a new xconf, says it can't make a backup).  On the same machine using WinXPpro S3 I get 1980x1200@60hz.

I saw a post with the same problem which was fixed by the following:
----------------------------
gtf 1920 1200 60

  # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
  Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync


ModeLine "1920x1200" 162 1920 1984 2176 2480 1200 1201 1204 1250 +hsync +vsync
----------------------------
I can get into the xconf file using the terminal and sudo, but since I'm really clueless I chicken-out on making the changes.  Could someone please provide me with a little hand-holding instructions on this?

Thanks in advance.

---

### Post by moe_syzlak on 2009-11-24
post your /etc/X11/xorg.conf

---


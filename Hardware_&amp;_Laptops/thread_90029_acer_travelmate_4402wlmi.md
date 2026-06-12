---
title: "acer travelmate 4402wlmi"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by NightVision on 2005-11-14
So I installed 5.10 x86_64.  Most evreything works :D:KS  except for

Wifi: i think it is a braodcom chipset? ip2200 drivers or something or am I confuzed?

3d aceleration on an ati x700 pci express.  Will this work with the drivers from ati's site?

---

### Post by NightVision on 2005-11-14
I have the fglrx installed now but it will not go higher than 1024x768...


 rarr@r00t:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

Any ideas?

---

### Post by Juzz on 2005-11-14
Check your resolutions in /etc/X11/xorg.conf perhaps 1024x768 is the highest resolution listed.

---

### Post by NightVision on 2005-11-14
I fixed it by reconfiguring xorg-x server and selecting "advanced" on the monitor configuration.  1280x800 now.:p  

All thats left is wifi and finding out how to resume after a hibernate.

---


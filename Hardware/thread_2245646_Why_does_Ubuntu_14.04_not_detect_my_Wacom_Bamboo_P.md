---
title: "Why does Ubuntu 14.04 not detect my Wacom Bamboo Pad CTH-301K (USB)?"
date: 2014-09-25
forum: Hardware
---

### Post by kamil-j-nizinski on 2014-09-25
When I plug in my tablet it does nothing and it is not detected by Wacom Tablet mode in Settings.
  I have already read tons of different threads, I have installed the Kernel Driver, and X Driver from this page [http://linuxwacom.sourceforge.net/wiki/index.php/Downloads](http://linuxwacom.sourceforge.net/wiki/index.php/Downloads) and created a file etc/X11/xorg.conf.d/50-wacom.conf exactly the same like this one here [http://sourceforge.net/p/linuxwacom/xf86-input-wacom/ci/master/tree/conf/50-wacom.conf](http://sourceforge.net/p/linuxwacom/xf86-input-wacom/ci/master/tree/conf/50-wacom.conf)
  There is no result. The only trace that the tablet is plugged in is that when I write lsusb in the terminal, the output is:


  `Bus 002 Device 005: ID 8087:07da Intel Corp. 
Bus 002 Device 094: ID 056a:0318 Wacom Co., Ltd  
Bus 002 Device 039: ID 062a:4102 Creative Labs  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 04f2:b302 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub `


  Please, help! I don't want to waste my money!

---


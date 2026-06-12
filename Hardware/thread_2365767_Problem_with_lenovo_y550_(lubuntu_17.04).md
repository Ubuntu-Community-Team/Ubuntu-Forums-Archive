---
title: "Problem with lenovo y550 (lubuntu 17.04)"
date: 2017-07-10
forum: Hardware
---

### Post by nicholas764 on 2017-07-10
Hello, everyone ! I come across a problem with my current configuration (lenovo y550-4-kc-b , nvidia gt m240). I installed Lubuntu 17.04 with Xfce. Grafic artifacts appear when I run applications like Chromium, Atom editor, Visual Studio Code with hardware acceleration. The problem has gone If I disable this option. Also I have artifacts with Unity on Ubuntu 14.04 and 16.04 (Unity), (17.04 - much more better). No artifacts with Xfce. I tried to install proprietary drivers (Nvidia legacy binary driver - version 304.135, Nvidia binary driver version 340.102). The system crashes (black screen when i reload). The last workible driver on windows 7  267.76 . I updated all drivers and software. How can i fix this issue ? It doesn't matter to me which driver to use - nouveau or proprietary.  


phoronix-test-suite system-info 


Hardware:
Processor: Intel Pentium T4400 @ 2.20GHz (2 Cores), Motherboard: LENOVO KIWB1, Chipset: Intel Mobile 4 MCH + ICH9M, Memory: 2048MB, Disk: 320GB Seagate ST320LM001 HN-M3, Graphics: NVA5 1024MB, Audio: Realtek ALC272, Network: Broadcom Limited NetLink BCM5784M Gigabit PCIe + Broadcom Limited BCM4312 802.11b/g


Software:
OS: Ubuntu 17.04, Kernel: 4.10.0-26-generic (i686), Desktop: Xfce 4.12, Display Driver: modesetting 1.19.3, OpenGL: 3.3 Mesa 17.2.0-devel, Compiler: GCC 6.3.0 20170406, File-System: ext4, Screen Resolution: 1366x768


cat /var/log/Xorg.0.log | egrep -i "(error|fail|warning)"


cat /var/log/Xorg.0.log | egrep -i "(error|fail|warning)"
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.674] (WW) Warning, couldn't open module nvidia
[    33.674] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    33.736] (WW) Warning, couldn't open module nvidia
[    33.736] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    33.737] (II) Failed to load module "nouveau" (already loaded, 0)
[    33.737] (II) Failed to load module "modesetting" (already loaded, 0)
[    33.737] (II) Failed to load module "fbdev" (already loaded, 0)
[    33.738] (II) Failed to load module "vesa" (already loaded, 0)

---

### Post by nicholas764 on 2017-07-11
any ideas ?:-(

---

### Post by nicholas764 on 2017-07-13
:sad:

---


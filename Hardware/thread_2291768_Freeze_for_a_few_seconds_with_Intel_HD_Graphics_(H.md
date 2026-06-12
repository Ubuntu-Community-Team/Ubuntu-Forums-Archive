---
title: "Freeze for a few seconds with Intel HD Graphics (Haswell) - Ubuntu 14.04"
date: 2015-08-22
forum: Hardware
---

### Post by arthur_8200 on 2015-08-22
Hi,

with my new Desktop PC I have got a driver problem with the video card, sometimes the screen freezes for a few seconds.
Mainboard: Asrock Z97 Extreme4
CPU with GPU: Intel Pentium G3258 (haswell) with Intel HD Graphics
Ubuntu: 14.04 LTS amd64 (Kernel: 3.16.0-46-generic #62~14.04.1-Ubuntu) with all latest updates

It's clean installation without modifying any display/xorg settings.

Attached part of the xorg and dmesg logfile.


Thank you!
[ATTACH]263994[/ATTACH]
[ATTACH]263995[/ATTACH]

---

### Post by arthur_8200 on 2015-09-07
Until now there is no improvement of the problem.
It's interesting that during the screen is freezed only the mouse can be moved. Input of the keyboard is getting recognized, because after the freeze the characters that were input have an effect.

---

### Post by kerry_s on 2015-09-07
i've seen that render ring error before, the fix is to switch to the uxa driver instead of sna. google creating a 20-intel.conf file.

---


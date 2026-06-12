---
title: "Shaky screen on ubuntu with Intel i3, h55 and integrated Intel Hd graphics"
date: 2011-04-27
forum: Hardware
---

### Post by AtteB on 2011-04-27
I just bought a shuttle sh55j2 with integrated Intel HD Graphics, Intel H55 Express Chipset and a Intel Core i3 Clarkdale processor. When I'm running xbmc-live 10.10 or 10.04.1 the screen is almost unreadable since it's shaky/fuzzy (from left to right). The same if a install the minimal ubuntu 10.10. The strange part is that the picture isn't shaky within the bios but when I get to the command prompt (before starting X) and also when started X. I've read tons of threads and tried a bunch of things but nothing has helped. Could someone help me or are my new computer aimed for windows only?

shuttle:~$ uname -a
Linux shuttle 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux
shuttle:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

### Post by AtteB on 2011-04-27
Hi

i just found out that my primary hdmi output works fine and its only my second output using vga to a 19 Hp monitor that are shaky. i guess it's the refresh rate or something put where do I adjust it since there is no xorg.conf anymore?

---


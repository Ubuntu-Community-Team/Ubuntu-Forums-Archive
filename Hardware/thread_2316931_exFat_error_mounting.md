---
title: "exFat error mounting"
date: 2016-03-12
forum: Hardware
---

### Post by valereguerin on 2016-03-12
[I]Error mounting system-managed device /dev/sde1: Command-line `mount "/mnt/5A8D-5C0C"' exited with non-zero exit status 1:
stdout: `FUSE exfat 1.0.1
'
stderr: `ERROR: unknown entry type 0xab.:confused:

```
freeman@freeman-Sniper:~$ inxi -b
your 131072x1 screen size is bogus. expect trouble
System:    Host: freeman-Sniper Kernel: 3.13.0-80-generic x86_64 (64 bit) Desktop: Gnome 3.10.4 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award version: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 CPU 930 (-HT-MCP-) clocked at 2860.248 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] 
           X.Org: 1.15.1 drivers: ati,fglrx (unloaded: fbdev,vesa,radeon) Resolution: 1920x1080@60.0hz 
           GLX Renderer: AMD Radeon HD 7900 Series GLX Version: 4.5.13399 - CPC 15.20.1013
Network:   Card-1: D-Link System DGE-528T Gigabit Ethernet Adapter driver: r8169 
           Card-2: Realtek RTL8187 Wireless Adapter driver: rtl8187 
Drives:    HDD Total Size: 5815.3GB (11.4% used)
Info:      Processes: 303 Uptime: 14:58 Memory: 2160.4/7982.7MB Client: Shell (bash) inxi: 1.9.17 

```

Thanks for regards,
[/I]

---

### Post by ajgreeny on 2016-03-12
If you have not already done so, use command ```
sudo apt-get install exfat-fuse exfat-utils
``` which should allow you to mount an exfat partition.

---

### Post by valereguerin on 2016-03-16
i already do it,  (no exotic package, no ppa, just ubuntu team update....on this config)

and the same thing with new Kernel install 4.5 rc...

---


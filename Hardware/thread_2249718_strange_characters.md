---
title: "strange characters"
date: 2014-10-24
forum: Hardware
---

### Post by pit.blkrv on 2014-10-24
Hello,

from time to time I'm getting strange characters displayed in different programms (thunderbird, firefox mostly). Often it is only one character which is crumbled, but all over the active window. I added some pictures, to show, what I mean.

I'm using trusty on that hardware:

```
System:    Host: ttpit-black Kernel: 3.13.0-37-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Intel model: DH67BL version: AAG10189-205
           Bios: Intel version: BLH6710H.86A.0160.2012.1204.1156 date: 12/04/2012
CPU:       Quad core Intel Core i5-2500 CPU (-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 26339.8 
           Clock Speeds: 1: 1600.00 MHz 2: 1600.00 MHz 3: 1600.00 MHz 4: 1600.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Bonaire XT [Radeon HD 7790/8770 / R9 260 OEM] bus-ID: 01:00.0 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1200@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD BONAIRE GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes
Audio:     Card-1: Advanced Micro Devices [AMD/ATI] Device aac0 driver: snd_hda_intel bus-ID: 01:00.1 
           Card-2: Intel 6 Series/C200 Series Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-37-generic
Network:   Card: Intel 82579V Gigabit Network Connection driver: e1000e ver: 2.3.2-k port: f040 bus-ID: 00:19.0
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: e0:69:95:3c:55:9e
Drives:    HDD Total Size: 2256.5GB (40.3% used) 1: id: /dev/sda model: WDC_WD20EZRX size: 2000.4GB 
           2: id: /dev/sdb model: Samsung_SSD_840 size: 256.1GB 
Partition: ID: / size: 59G used: 29G (52%) fs: ext4 ID: swap-1 size: 12.65GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 204 Uptime: 1:51 Memory: 2081.8/7963.0MB Runlevel: 2 Gcc sys: 4.8.2 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 

```

I thought it's an hardware issue, maybe. I used the newest Catalyst-Driver for some time, the strange characters did not appear then, but the system froze from time to time. So this was no solution :-(
I switched back to the radeon driver, which is stable.

It would be great to get rid of this strange characters ....

Any ideas???

pit

---


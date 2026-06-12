---
title: "CPU stuck at 1600mhz AC/800mhz on battery"
date: 2014-06-05
forum: Hardware
---

### Post by martin022 on 2014-06-05
Hi, i have recently installed xubuntu 14.04 on thinkpad t400 (core 2 duo P8600 2.4GHz with switchable graphics, 6gb ram, 120GB ssd). right after installation everything worked fine, so i installed some software, updates and restart it. now even when i set 2.4GHz with indicator-cpufreq it stay at 1,6/0.8GHz. i had same problem on windows, but only on battery it stuck at 800mhz. i think that it have something with intel speedstep "technology".. does somebody had same problem? how can i fix that?

> x@xx:~$ inxi -F
System:    Host: xx Kernel: 3.13.0-27-generic x86_64 (64 bit) Desktop: Xfce 4.11.6 Distro: Ubuntu 14.04 trusty
Machine:   System: LENOVO product: 2767A26 version: ThinkPad T400
           Mobo: LENOVO model: 2767A26 Bios: LENOVO version: 7UET94WW (3.24 ) date: 10/17/2012
CPU:       Dual core Intel Core2 Duo CPU P8600 (-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) 
           Clock Speeds: 1: 1600.00 MHz 2: 1600.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470] 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1280x1024@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD RV620 GLX Version: 3.0 Mesa 10.1.3
Audio:     Card-1: Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel Sound: ALSA ver: k3.13.0-27-generic
           Card-2: C-Media CM106 Like Sound Device driver: USB Audio 
Network:   Card-1: Intel Ultimate N WiFi Link 5300 driver: iwlwifi 
           IF: wlan0 state: up mac: 00:16:ea:ed:bb:82
           Card-2: Intel 82567LM Gigabit Network Connection driver: e1000e 
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: 00:1c:25:98:36:c2
Drives:    HDD Total Size: 280.1GB (3.6% used) 1: id: /dev/sda model: KINGSTON_SVP200S size: 120.0GB 
           2: id: /dev/sdb model: WDC_WD1600BEVT size: 160.0GB 
Partition: ID: / size: 105G used: 9.3G (10%) fs: ext4 ID: swap-1 size: 6.37GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 54.0C mobo: 53.0C 
           Fan Speeds (in rpm): cpu: 3435 
Info:      Processes: 203 Uptime: 10:03 Memory: 1775.0/5899.6MB Client: Shell (bash) inxi: 1.9.17

---

### Post by martin022 on 2014-06-05
SOLVED, i just went to bios and change "on battery CPU management" to Automatic or something instead of Maximum power.

---


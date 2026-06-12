---
title: "XPS 9360 Graphics very slow after Bionic Beaver upgrade"
date: 2018-09-24
forum: Hardware
---

### Post by dagger10k on 2018-09-24
Hi, I apologize if this has already been asked, but I couldn't find anything.

I bought a Dell XPS 13 Developer Edition 9360, which came with Ubuntu 16.04, which I manually reinstalled from scratch at some point.

Everything worked just fine. However, when Bionic Beaver came out, I decided to upgrade. I immediately noticed that the graphics performance went way down, most noticeably when trying to play games or watch video. 

Youtube videos are choppy, and sometimes completely grind to a halt. I also noticed that the CPU usage for the chrome tab running the video will usually go from ~20% to ~140% when paused versus playing.

It seems like the GPU (Intel HD 620) is no longer being used, and all graphics are being handled by the CPU instead, but as far as I can tell, the graphics drivers are correctly installed.

Does anyone have any other ideas of what I could look at?

```

james@james-XPS-13-9360:~$ inxi -Fz
System:    Host: james-XPS-13-9360 Kernel: 4.15.0-34-generic x86_64 bits: 64 Desktop: Gnome 3.28.3
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: Dell product: XPS 13 9360 serial: N/A
           Mobo: Dell model: 06CC14 v: A00 serial: N/A UEFI: Dell v: 2.9.0 date: 07/09/2018
Battery    BAT0: charge: 34.8 Wh 59.9% condition: 58.1/60.0 Wh (97%)
CPU:       Dual core Intel Core i7-7500U (-MT-MCP-) cache: 4096 KB
           clock speeds: max: 3500 MHz 1: 900 MHz 2: 900 MHz 3: 905 MHz 4: 955 MHz
Graphics:  Card: Intel HD Graphics 620
           Display Server: wayland (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 3200x1800@59.96hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2) version: 4.5 Mesa 18.0.5
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel Sound: ALSA v: k4.15.0-34-generic
Network:   Card: Intel Wireless 8260 driver: iwlwifi
           IF: wlp58s0 state: up mac: <filter>
Drives:    HDD Total Size: 512.1GB (14.1% used)
           ID-1: /dev/nvme0n1 model: PC300_NVMe_SK_hynix_512GB size: 512.1GB
Partition: ID-1: / size: 454G used: 53G (13%) fs: ext4 dev: /dev/nvme0n1p2
           ID-2: swap-1 size: 17.06GB used: 0.00GB (0%) fs: swap dev: /dev/dm-0
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 46.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 273 Uptime: 13 days Memory: 4127.9/15767.9MB Client: Shell (bash) inxi: 2.3.56 

james@james-XPS-13-9360:~$ lspci -nnk | grep -i VGA -A3
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 620 [8086:5916] (rev 02)
    Subsystem: Dell HD Graphics 620 [1028:075b]
    Kernel driver in use: i915
    Kernel modules: i915

```

---


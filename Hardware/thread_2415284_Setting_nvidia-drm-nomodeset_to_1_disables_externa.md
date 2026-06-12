---
title: "Setting nvidia-drm-nomodeset to 1 disables external monitor detection!"
date: 2019-03-23
forum: Hardware
---

### Post by Jason_Marlow on 2019-03-23
I've bounced around between a few different distros trying to find a solution to my dGPU/external monitor woes. I've landed on Pop!_OS 18.10 because of its awesome graphics switching feature. When I set it to Nvidia graphics (I'm using a ThinkPad x1 Extreme with a GTX 1050 ti GPU) it has a pretty gnarly screen tearing problem. So I did what every Ubuntu noob does and googled it and followed a guide, specifically this one: [http://ubuntuhandbook.org/index.php/2018/07/fix-screen-tearing-ubuntu-18-04-optimus-laptops/](http://ubuntuhandbook.org/index.php/2018/07/fix-screen-tearing-ubuntu-18-04-optimus-laptops/)

Worked out pretty well. Only when I plugged in my external monitor (via thunderbolt to DisplayPort) it isn't even recognized. I found mutterings of this problem in other places but I found no real dependable way to solve this issue. Can I get tear-free nvidia graphics (i'm using proprietary drivers) AND the ability to plug in external displays?

---

### Post by Jason_Marlow on 2019-03-23
Quick note: I saw this post, [https://ubuntuforums.org/showthread.php?t=2390319](https://ubuntuforums.org/showthread.php?t=2390319)

I don't want to mess with installing new display managers. Last time I tried that it messed up my graphics card switching capabilities. I also don't know if I want ot create an xorg.conf file in my /etc/X11 directory, as that interferes with graphics switching as well. I don't get tearing when I run on intel graphics. So is there any way at all I can have the fix run only when I have nvidia graphics enabled? My external monitor can only work in that case anyway, since those ports are linked directly to the GPU anyway.

---

### Post by him610 on 2019-03-24
We need to know something about your system. Laptop? Please show results, between code tags, of *inxi -F*

---

### Post by Jason_Marlow on 2019-03-24
```

System:
  Host: pop-os Kernel: 4.18.0-16-generic x86_64 bits: 64 
  Desktop: Gnome 3.30.2 Distro: Pop!_OS 18.10 
Machine:
  Type: Laptop System: LENOVO product: 20MF000BUS v: ThinkPad X1 Extreme 
  serial: R90T59YT 
  Mobo: LENOVO model: 20MF000BUS v: SDK0R32862 WIN serial: W1KS92D10JK 
  UEFI: LENOVO v: N2EET36W (1.18 ) date: 01/08/2019 
Battery:
  ID-1: BAT0 charge: 77.5 Wh condition: 77.5/80.4 Wh (96%) 
CPU:
  Topology: 6-Core model: Intel Core i7-8750H bits: 64 type: MT MCP 
  L2 cache: 9216 KiB 
  Speed: 3189 MHz min/max: 800/4100 MHz Core speeds (MHz): 1: 1425 2: 1819 
  3: 1535 4: 1812 5: 1805 6: 1522 7: 1488 8: 1175 9: 1304 10: 1515 11: 1592 
  12: 1584 
Graphics:
  Device-1: Intel driver: i915 v: kernel 
  Device-2: NVIDIA GP107M [GeForce GTX 1050 Ti Mobile] driver: nvidia 
  v: 418.43 
  Display: server: X.Org 1.20.1 driver: modesetting,nvidia 
  unloaded: fbdev,nouveau,vesa resolution: 3440x1440~100Hz, 1920x1080~60Hz 
  OpenGL: renderer: GeForce GTX 1050 Ti with Max-Q Design/PCIe/SSE2 
  v: 4.6.0 NVIDIA 418.43 
Audio:
  Device-1: Intel Cannon Lake PCH cAVS driver: snd_hda_intel 
  Device-2: NVIDIA GP107GL High Definition Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k4.18.0-16-generic 
Network:
  Device-1: Intel Wireless-AC 9560 [Jefferson Peak] driver: iwlwifi 
  IF: wlp0s20f3 state: up mac: 48:f1:7f:83:a5:2c 
  Device-2: Intel Ethernet I219-V driver: e1000e 
  IF: enp0s31f6 state: down mac: 48:2a:e3:30:7a:0a 
  IF-ID-1: tun0 state: unknown speed: 10 Mbps duplex: full mac: N/A 
Drives:
  Local Storage: total: 476.94 GiB used: 58.81 GiB (12.3%) 
  ID-1: /dev/nvme0n1 vendor: Western Digital 
  model: PC SN720 SDAQNTW-512G-1001 size: 476.94 GiB 
Partition:
  ID-1: / size: 460.10 GiB used: 56.35 GiB (12.2%) fs: ext4 
  dev: /dev/nvme0n1p3 
  ID-2: swap-1 size: 4.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-0 
Sensors:
  System Temperatures: cpu: 58.0 C mobo: N/A gpu: nvidia temp: 47 C 
  Fan Speeds (RPM): cpu: 2769 
Info:
  Processes: 424 Uptime: 1h 08m Memory: 15.13 GiB used: 5.35 GiB (35.4%) 
  Shell: bash inxi: 3.0.24 



```

---

### Post by bobbyv2 on 2019-03-29
I have the exact same issue with my ThinkPad X1 Extreme.  GTX 1050Ti.  I've tried the "ForceCompositionPipeline" without success.  The only thing that works is setting the modeset=1, but that disables any external monitors.

---


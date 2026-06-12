---
title: "Will there be support for AMD A8-7410 GPU in Ubuntu 17.04 or later?"
date: 2017-11-21
forum: Hardware
---

### Post by deepakdeshp on 2017-11-21
Hello,

What is the chance that AMD 7410 APU will be supported in Ubuntu?

My configuration is

 ```
Machine:   System: Hewlett-Packard product: HP Notebook v: Type1ProductConfigId           Mobo: Hewlett-Packard model: 80CC v: 99.50
           Bios: Insyde v: F.22 date: 07/25/2016
CPU:       Quad core AMD A8-7410 APU with AMD Radeon R5 Graphics (-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 17567
           clock speeds: max: 2200 MHz 1: 2000 MHz 2: 1000 MHz 3: 1000 MHz
           4: 1000 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
           bus-ID: 00:01.0
           Card-2: Advanced Micro Devices [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330]
           bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: ati (unloaded: fbdev,vesa,radeon)
           Resolution: 1366x768@60.02hz
           GLX Renderer: Gallium 0.4 on AMD MULLINS (DRM 2.49.0 / 4.9.61-040961-generic, LLVM 4.0.0)
           GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel bus-ID: 00:14.2
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel bus-ID: 00:01.1
           Sound: Advanced Linux Sound Architecture v: k4.9.61-040961-generic
Network:   Card-1: Realtek RTL8723BE PCIe Wireless Network Adapter
           driver: rtl8723be port: 3000 bus-ID: 02:00.0
           IF: wlo1 state: up mac: <filter>
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 03:00.0
           IF: enp3s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (20.1% used)
           ID-1: /dev/sda model: HGST_HTS545050A7 size: 500.1GB
Partition: ID-1: / size: 61G used: 45G (79%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 5.35GB used: 0.00GB (0%) fs: swap dev: /dev/sda8
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 52.0C mobo: 20.0C gpu: N/A,43.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 263 Uptime: 9:00 Memory: 3074.9/6919.3MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.1
           Client: Shell (bash 4.3.481) inxi: 2.2.35
```

---

### Post by cpatrick08 on 2017-11-29
You have to use the open source drivers

---

### Post by kurt18947 on 2017-11-29
Have you booted a live USB or DVD to see what does and doesn't work? That should be a reasonable place to start. Performance may be a bit sluggish but at least you'll have an idea about wifi, audio, hot keys, that sort of thing.

---

### Post by metalbiker on 2017-12-25
Check the 'additional drivers' tab in software and updates and make sure to select the appropriate driver (try to use the open source driver) and then apply changes.

---

### Post by oldos2er on 2017-12-27
Thread moved to Hardware.

---


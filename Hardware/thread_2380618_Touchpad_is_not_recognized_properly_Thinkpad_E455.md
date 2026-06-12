---
title: "Touchpad is not recognized properly Thinkpad E455"
date: 2017-12-19
forum: Hardware
---

### Post by yoshiki2 on 2017-12-19
For some reason my touchpad does not work properly. 



alfredo@alfredo-ThinkPad-E455 ~ $ inxi -Fxz
System:    Host: alfredo-ThinkPad-E455 Kernel: 4.10.0-42-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: MATE 1.18.0 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Linux Mint 18.3 Sylvia
Machine:   System: LENOVO (portable) product: 20DE001PUS v: ThinkPad E455
           Mobo: LENOVO model: 20DE001PUS v: SDK0E50510 WIN
           Bios: LENOVO v: HTET52WW (1.24 ) date: 09/18/2017
CPU:       Dual core AMD A6-7000 Radeon R4 5 Compute Cores 2C+3G (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 8783
           clock speeds: max: 2200 MHz 1: 2200 MHz 2: 2200 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Kaveri [Radeon R4 Graphics]
           bus-ID: 00:01.0
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Gallium 0.4 on AMD KAVERI (DRM 2.49.0 / 4.10.0-42-generic, LLVM 4.0.0)
           GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel bus-ID: 00:14.2
           Card-2 Advanced Micro Devices [AMD/ATI] Kaveri HDMI/DP Audio Controller
           driver: snd_hda_intel bus-ID: 00:01.1
           Sound: Advanced Linux Sound Architecture v: k4.10.0-42-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 1000 bus-ID: 01:00.0
           IF: enp1s0 state: down mac: <filter>
           Card-2: Intel Device 24fd driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: up speed: N/A duplex: N/A mac: <filter>
Drives:    HDD Total Size: 120.0GB (41.2% used)
           ID-1: /dev/sda model: SATA_SSD size: 120.0GB
Partition: ID-1: / size: 96G used: 32G (36%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 15.92GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 51.8C mobo: N/A gpu: 51.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 166 Uptime: 5 min Memory: 1314.5/14861.3MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 
alfredo@alfredo-ThinkPad-E455 ~ $ 


Any ideas?

---


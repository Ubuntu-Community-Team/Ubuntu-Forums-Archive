---
title: "Poor quality screen at 1920x1080 with Ubuntu 19"
date: 2018-10-21
forum: Hardware
---

### Post by steveis2 on 2018-10-21
Hi,
  When I recently installed Ubuntu18.04 it launched with the nouveau driver rather than the Nvidia one and at 1920x1080. If I switched to the Nvidia driver I could only get a resolution of 1600x1200. I think this is because, for whatever reason, the system when using an Nvidia driver does not pick up the EDID (monitor characteristics) from the monitor (an Acer K222HQL). The cure as I found on Linux Mint 18.3 is to save the EDID when using the nouveau driver and use it as a custom EDID when using the Nvidia driver with the monitors actual vert and horiz sync settings. So far so good. 
  When I had done this the available resolutions increased and I can get 1920x1080 but the image is very poor in Ubuntu 18.04. The image is slightly out of focus and there is colour fringing on text and edges. Using LM18.3 I did not have this problem but Ubuntu 18.04 is a newer system than the one LM18.3 is based on and probably leads to different issues.
  Has anyone else had any problem similar to this and can anyone suggest a possible solution?

Regards Steve


System information
```
System:    Host: budgie-A320M-HD2 Kernel: 4.15.0-36-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.3 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: Gigabyte product: A320M-HD2 serial: N/A
           Mobo: Gigabyte model: A320M-HD2-CF v: x.x serial: N/A
           UEFI [Legacy]: American Megatrends v: F23 date: 08/08/2018
CPU:       Quad core AMD Athlon X4 950 (-MCP-) 
           arch: Excavator rev.1 cache: 4096 KB
           
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 27946
           clock speeds: max: 3500 MHz 1: 1837 MHz 2: 1483 MHz 3: 1716 MHz
           4: 1431 MHz
Graphics:  Card: NVIDIA GP107 [GeForce GTX 1050 Ti] bus-ID: 08:00.0
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia
           Resolution: 1600x1200@60.00hz
           OpenGL: renderer: GeForce GTX 1050 Ti/PCIe/SSE2
           version: 4.6.0 NVIDIA 390.77 Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] Device 157a
           driver: snd_hda_intel bus-ID: 00:09.2
           Card-2 NVIDIA GP107GL High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 08:00.1
           Sound: Advanced Linux Sound Architecture v: k4.15.0-36-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 03:00.0
           IF: enp3s0 state: down mac: <filter>
           Card-2: Realtek RTL8188EUS 802.11n Wireless Network Adapter
           usb-ID: 004-003
           IF: N/A state: N/A mac: N/A
Drives:    HDD Total Size: 1360.3GB (1.6% used)
           ID-1: /dev/sda model: ST1000DM010 size: 1000.2GB
           ID-2: /dev/sdb model: KINGSTON_SA400S3 size: 120.0GB
           ID-3: /dev/sdc model: KINGSTON_SA400S3 size: 240.1GB
Partition: ID-1: / size: 212G used: 6.0G (3%) fs: ext4 dev: /dev/sdc1
           ID-2: swap-1 size: 7.80GB used: 0.00GB (0%)
           fs: swap dev: /dev/sdc5
           ID-3: swap-2 size: 7.94GB used: 0.00GB (0%)
           fs: swap dev: /dev/sdb5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 0.0C mobo: N/A gpu: 0.0:30C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 215 Uptime: 18 min Memory: 1231.4/6983.0MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 

```

---


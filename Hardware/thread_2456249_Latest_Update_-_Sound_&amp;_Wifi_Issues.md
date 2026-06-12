---
title: "Latest Update - Sound &amp; Wifi Issues"
date: 2021-01-07
forum: Hardware
---

### Post by halw on 2021-01-07
The latest update, done today 7 January 2021, has caused issues with sound and the 5.8 kernel does not see wifi.
Below are system specs. After having issues, I did a Timeshift restore is listed re. kernel and whatever else is applicable.
```
System:
  Host: Ryzen7 Kernel: 5.4.0-59-generic x86_64 bits: 64 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: ASUSTeK model: ROG STRIX X370-F GAMING v: Rev X.0x 
  serial: <superuser/root required> UEFI: American Megatrends v: 5406 
  date: 11/13/2019 
CPU:
  Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP 
  L2 cache: 4096 KiB 
  Speed: 1374 MHz min/max: 1550/3000 MHz Core speeds (MHz): 1: 1374 2: 1371 
  3: 1372 4: 1445 5: 1371 6: 1375 7: 1372 8: 1375 9: 1374 10: 1453 11: 1375 
  12: 1373 13: 1375 14: 1374 15: 1375 16: 1375 
Graphics:
  Device-1: NVIDIA GP106 [GeForce GTX 1060 6GB] driver: nvidia v: 450.80.02 
  Display: x11 server: X.Org 1.20.8 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 2560x1440~60Hz 
  OpenGL: renderer: GeForce GTX 1060 6GB/PCIe/SSE2 v: 4.6.0 NVIDIA 450.80.02 
Audio:
  Device-1: NVIDIA GP106 High Definition Audio driver: snd_hda_intel 
  Device-2: AMD Family 17h HD Audio driver: snd_hda_intel 
  Device-3: Logitech OrbiCam type: USB driver: snd-usb-audio,uvcvideo 
  Sound Server: ALSA v: k5.4.0-59-generic 
Network:
  Device-1: Intel I211 Gigabit Network driver: igb 
  IF: enp5s0 state: down mac: b0:6e:bf:c7:2b:2d 
  Device-2: Broadcom and subsidiaries BCM4360 802.11ac Wireless Network 
  Adapter 
  driver: wl 
  IF: wlp9s0 state: up mac: 1c:87:2c:b8:0f:f8 
Drives:
  Local Storage: total: 1.64 TiB used: 48.62 GiB (2.9%) 
  ID-1: /dev/nvme0n1 vendor: A-Data model: SX8200PNP size: 953.87 GiB 
  ID-2: /dev/sda vendor: Crucial model: CT525MX300SSD1 size: 489.05 GiB 
  ID-3: /dev/sdb vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
Partition:
  ID-1: / size: 937.40 GiB used: 48.62 GiB (5.2%) fs: ext4 
  dev: /dev/nvme0n1p2 
Sensors:
  System Temperatures: cpu: 32.8 C mobo: N/A gpu: nvidia temp: 46 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 0% 
Info:
  Processes: 375 Uptime: 12m Memory: 31.36 GiB used: 1.64 GiB (5.2%) 
  Shell: bash inxi: 3.0.38 
```

---

### Post by wmcl on 2021-01-08
My sound stopped working with the last kernel update, too. Also an AMD Family 17h audio controller. Tried booting into older kernels, graphics didn't work with the previous 5.8 version, so I booted into 5.4.0-60-generic. Sound is working with this one. Can't help with the WiFi, since this is on a PC with ethernet.

---


---
title: "Second monitor does not work with newer kernel"
date: 2022-05-11
forum: Hardware
---

### Post by fermiy on 2022-05-11
Hi!
I stuck with old kernel for quite a while, my second screen connected with dock station did not work with any new kernels. 
Now it seems there is some configuration change that prevents older kernel use. Does anybody know how to debug this issue?
5.11.0-27 I think that one only worked. I use Intel graphics by default

System:
  Kernel: 5.13.0-40-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.4 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: HP product: HP ZBook 15 G6 v: N/A serial: <filter> 
  Mobo: HP model: 860F v: KBC Version 65.34.00 serial: <filter> UEFI: HP 
  v: R92 Ver. 01.12.21 date: 03/25/2022 
Battery:
  ID-1: BAT0 charge: 68.2 Wh condition: 68.2/90.0 Wh (76%) 
  model: Hewlett-Packard Primary status: Full 
  Device-1: hidpp_battery_0 
  model: Logitech Wireless Mobile Mouse MX Anywhere 2S 
  charge: 55% (should be ignored) status: Discharging 
CPU:
  Topology: 6-Core model: Intel Core i7-9850H bits: 64 type: MT MCP 
  arch: Kaby Lake rev: D L2 cache: 12.0 MiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 62399 
  Speed: 900 MHz min/max: 800/1800 MHz Core speeds (MHz): 1: 900 2: 900 
  3: 900 4: 900 5: 897 6: 900 7: 900 8: 900 9: 900 10: 901 11: 900 12: 900 
Graphics:
  Device-1: Intel UHD Graphics 630 vendor: Hewlett-Packard driver: i915 
  v: kernel bus ID: 00:02.0 
  Device-2: NVIDIA TU106GLM [Quadro RTX 3000 Mobile / Max-Q] 
  vendor: Hewlett-Packard driver: N/A bus ID: 01:00.0 
  Display: server: X.Org 1.20.13 driver: fbdev unloaded: modesetting,vesa 
  resolution: 3840x2160~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2) 
  v: 4.6 Mesa 22.2.0-devel (git-7a6d852 2022-05-05 focal-oibaf-ppa) 
  direct render: Yes 
Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: Hewlett-Packard 
  driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
  Device-2: NVIDIA TU106 High Definition Audio vendor: Hewlett-Packard 
  driver: snd_hda_intel v: kernel bus ID: 01:00.1 
  Device-3: GN Netcom Jabra UC Voice 750 MS type: USB 
  driver: jabra,snd-usb-audio,usbhid bus ID: 5-1.3.1:5 
  Device-4: HP type: USB driver: hid-generic,snd-usb-audio,usbhid 
  bus ID: 5-1.3.5:7 
  Sound Server: ALSA v: k5.13.0-40-generic 
Network:
  Device-1: Intel Ethernet I219-LM vendor: Hewlett-Packard driver: e1000e 
  v: kernel port: efa0 bus ID: 00:1f.6 
  IF: enp0s31f6 state: down mac: <filter> 
  Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi v: kernel port: 4000 
  bus ID: 70:00.0 
  IF: wlp112s0 state: down mac: <filter> 
  Device-3: Realtek RTL8153 Gigabit Ethernet Adapter type: USB driver: r8152 
  bus ID: 6-1.3.3:4 
  IF: enx3822e232f39a state: up speed: 1000 Mbps duplex: full mac: <filter> 
  IF-ID-1: docker0 state: down mac: <filter> 
Drives:
  Local Storage: total: 476.94 GiB used: 222.83 GiB (46.7%) 
  ID-1: /dev/nvme0n1 vendor: Western Digital 
  model: PC SN720 SDAPNTW-512G-1006 size: 476.94 GiB 
Partition:
  ID-1: / size: 239.31 GiB used: 222.75 GiB (93.1%) fs: ext4 
  dev: /dev/nvme0n1p4 
Sensors:
  System Temperatures: cpu: 62.0 C mobo: 55.0 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 426 Uptime: 1h 31m Memory: 46.84 GiB used: 4.81 GiB (10.3%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38

---

### Post by fermiy on 2022-05-12
It seems once I left only Intel gpu in BIOS, second monitor started to work. I will try other options since I want to use Nvidia sometimes. In my case it seems that disabled Nvidia got outout for the second monitor and it did not appear for Intel and since Nvidia disabled was lost. Does anybody know how to assign it to Intel by default?

---


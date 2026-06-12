---
title: "Black screen after waking up desktop from suspend mode"
date: 2022-01-23
forum: Hardware
---

### Post by atactic on 2022-01-23
Have seen several similar issues reported but none really identical.
In my Ubuntu 20.04 desktop environment, screen is black (no signal) after waking up from suspend mode.
Problem was not present before, not idea which updates or apps may have caused this issue.

System:
  Kernel: 5.11.0-46-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: Gigabyte model: Z97X-UD5H v: x.x serial: <filter> 
  UEFI: American Megatrends v: F10 date: 08/03/2015 
CPU:
  Topology: Quad Core model: Intel Core i7-4790 bits: 64 type: MT MCP 
  arch: Haswell rev: 3 L2 cache: 8192 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 57472 
  Speed: 1328 MHz min/max: 800/4000 MHz Core speeds (MHz): 1: 1059 2: 1731 
  3: 1070 4: 1250 5: 1037 6: 1136 7: 998 8: 1325 
Graphics:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics 
  vendor: Gigabyte driver: i915 v: kernel bus ID: 00:02.0 
  Device-2: NVIDIA GM200 [GeForce GTX TITAN X] vendor: eVga.com. 
  driver: nvidia v: 460.91.03 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.13 driver: modesetting,nvidia 
  unloaded: fbdev,nouveau,vesa resolution: 3840x2160~60Hz, 3840x2160~60Hz 
  OpenGL: renderer: GeForce GTX TITAN X/PCIe/SSE2 v: 4.6.0 NVIDIA 460.91.03 
  direct render: Yes 
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio 
  driver: snd_hda_intel v: kernel bus ID: 00:03.0 
  Device-2: Intel 9 Series Family HD Audio vendor: Gigabyte 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Device-3: NVIDIA GM200 High Definition Audio vendor: eVga.com. 
  driver: snd_hda_intel v: kernel bus ID: 01:00.1 
  Device-4: C-Media CMI8788 [Oxygen HD Audio] vendor: ASUSTeK Virtuoso 100 
  driver: snd_virtuoso v: kernel bus ID: 08:04.0 
  Device-5: Logitech Headset H340 type: USB 
  driver: hid-generic,snd-usb-audio,usbhid bus ID: 3-6:3 
  Device-6: Microsoft LifeCam HD-3000 type: USB 
  driver: snd-usb-audio,uvcvideo bus ID: 3-10:6 
  Sound Server: ALSA v: k5.11.0-46-generic 
Network:
  Device-1: Intel Ethernet I217-V vendor: Gigabyte driver: e1000e v: kernel 
  port: f080 bus ID: 00:19.0 
  IF: eno1 state: down mac: <filter> 
  Device-2: Broadcom and subsidiaries BCM4360 802.11ac Wireless Network 
  Adapter 
  vendor: ASUSTeK driver: wl v: kernel port: e000 bus ID: 02:00.0 
  IF: wlp2s0 state: up mac: <filter> 
  Device-3: Qualcomm Atheros Killer E220x Gigabit Ethernet vendor: Gigabyte 
  driver: alx v: kernel port: d000 bus ID: 04:00.0 
  IF: enp4s0 state: down mac: <filter> 
  IF-ID-1: ipv6leakintrf0 state: unknown speed: N/A duplex: N/A 
  mac: <filter> 
  IF-ID-2: proton0 state: unknown speed: 10 Mbps duplex: full mac: N/A 
Drives:
  Local Storage: total: 931.51 GiB used: 775.29 GiB (83.2%) 
  ID-1: /dev/nvme0n1 vendor: Smart Modular Tech. model: SHGP31-1000GM-2 
  size: 931.51 GiB 
Partition:
  ID-1: / size: 913.74 GiB used: 775.00 GiB (84.8%) fs: ext4 dev: /dev/dm-1 
  ID-2: /boot size: 704.5 MiB used: 288.8 MiB (41.0%) fs: ext4 
  dev: /dev/nvme0n1p2 
  ID-3: swap-1 size: 976.0 MiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-2 
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C gpu: nvidia temp: 69 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 29% 
Info:
  Processes: 429 Uptime: 26m Memory: 31.18 GiB used: 5.38 GiB (17.3%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38

---

### Post by koppr on 2022-02-21
I have had this problem with a GTX 970 card following an upgrade of the accelerated driver to the 470 version. Suspend works normally with Debian Bookworm, a similar Linux distro, which is also upgraded to the latest version. Both OS use GNOME as the DE.

---


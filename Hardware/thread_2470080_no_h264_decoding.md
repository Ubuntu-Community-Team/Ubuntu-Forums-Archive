---
title: "no h264 decoding"
date: 2021-12-19
forum: Hardware
---

### Post by KOUTRONAS_Mixalis on 2021-12-19
hi i have a r600 rs780l gpu i have updated my mesa drivers when i type vainfo h264 is not supported ```
libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/r600_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.7 (libva 2.6.0)
vainfo: Driver version: Mesa Gallium driver 21.0.3 for AMD RS780 (DRM 2.50.0 / 5.11.0-43-generic, LLVM 12.0.0)
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc

```
```
System:
  Kernel: 5.11.0-43-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 wm: gnome-shell dm: GDM3 3.36.3 
  Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: ASRock model: 760GM-HDV serial: <filter> 
  BIOS: American Megatrends v: P1.20 date: 05/11/2018 
CPU:
  Topology: 8-Core model: AMD FX-8370 bits: 64 type: MCP arch: Bulldozer 
  L2 cache: 2048 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 63858 
  Speed: 1396 MHz min/max: 1400/4000 MHz boost: enabled Core speeds (MHz): 
  1: 1782 2: 1461 3: 1562 4: 1395 5: 1489 6: 1396 7: 1720 8: 1629 
Graphics:
  Device-1: AMD RS780L [Radeon 3000] vendor: ASRock driver: radeon v: kernel 
  bus ID: 01:05.0 chip ID: 1002:9616 
  Display: x11 server: X.Org 1.20.13 driver: radeon compositor: gnome-shell 
  resolution: 1440x900~60Hz 
  OpenGL: renderer: AMD RS780 (DRM 2.50.0 / 5.11.0-43-generic LLVM 12.0.0) 
  v: 3.3 Mesa 21.0.3 compat-v: 3.0 direct render: Yes 
Audio:
  Device-1: AMD SBx00 Azalia vendor: ASRock driver: snd_hda_intel v: kernel 
  bus ID: 00:14.2 chip ID: 1002:4383 
  Device-2: AMD RS780 HDMI Audio [Radeon 3000/3100 / HD 3200/3300] 
  vendor: ASRock driver: snd_hda_intel v: kernel bus ID: 01:05.1 
  chip ID: 1002:960f 
  Sound Server: ALSA v: k5.11.0-43-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: ASRock driver: r8169 v: kernel port: e800 bus ID: 02:00.0 
  chip ID: 10ec:8168 
  IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 465.76 GiB used: 8.37 GiB (1.8%) 
  ID-1: /dev/sda type: USB vendor: Seagate model: ST350041 3AS 
  size: 465.76 GiB serial: <filter> rev: 3202 scheme: MBR 
Partition:
  ID-1: / size: 17.91 GiB used: 8.37 GiB (46.7%) fs: ext4 dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 28.2 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Repos:
  Active apt repos in: /etc/apt/sources.list 
  1: deb http://gr.archive.ubuntu.com/ubuntu/ focal main restricted
  2: deb http://gr.archive.ubuntu.com/ubuntu/ focal-updates main restricted
  3: deb http://gr.archive.ubuntu.com/ubuntu/ focal universe
  4: deb http://gr.archive.ubuntu.com/ubuntu/ focal-updates universe
  5: deb http://gr.archive.ubuntu.com/ubuntu/ focal multiverse
  6: deb http://gr.archive.ubuntu.com/ubuntu/ focal-updates multiverse
  7: deb http://gr.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
  8: deb http://security.ubuntu.com/ubuntu focal-security main restricted
  9: deb http://security.ubuntu.com/ubuntu focal-security universe
  10: deb http://security.ubuntu.com/ubuntu focal-security multiverse
Info:
  Processes: 275 Uptime: 29m Memory: 15.37 GiB used: 2.25 GiB (14.7%) 
  Init: systemd v: 245 runlevel: 5 Compilers: gcc: N/A Shell: bash v: 5.0.17 
  running in: gnome-terminal inxi: 3.0.38 

```

---


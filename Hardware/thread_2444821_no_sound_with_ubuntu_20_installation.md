---
title: "no sound with ubuntu 20 installation"
date: 2020-06-04
forum: Hardware
---

### Post by smokeyone2 on 2020-06-04
Hello
I have searched for ages vis google/forums for an answer to the no sound problem and have tried lots of ideas without success. I have even tested different/older distributions with no luck.

I hope the info below assists

sudo apt install inxi
inxi -Fxz


system:
  Kernel: 5.4.0-33-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Detachable System: SAMSUNG product: Galaxy Book 12 v: P04HAC 
  serial: <filter> 
  Mobo: SAMSUNG model: SAMSUNG_NP1234567890 
  v: SAMSUNG_SW_REVISION_12345+0.0.0000 serial: <filter> 
  UEFI: American Megatrends v: P04HAC.000.180220.WY.1219 date: 02/20/2018 
Battery:
  ID-1: BAT1 charge: 29.1 Wh condition: 39.3/39.0 Wh (101%) 
  model: SAMSUNG Electronics SR Real Battery status: Charging 
CPU:
  Topology: Dual Core model: Intel Core i5-7200U bits: 64 type: MT MCP 
  arch: Amber Lake rev: 9 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 21599 
  Speed: 500 MHz min/max: 400/3100 MHz Core speeds (MHz): 1: 500 2: 500 
  3: 500 4: 500 
Graphics:
  Device-1: Intel HD Graphics 620 vendor: Samsung Co driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 2160x1440~60Hz 
  OpenGL: renderer: Mesa Intel HD Graphics 620 (KBL GT2) v: 4.6 Mesa 20.0.4 
  direct render: Yes 
Audio:
  Device-1: Intel Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging 
  Unit 
  vendor: Samsung Co driver: ipu3-imgu bus ID: 00:05.0 
  Device-2: Intel vendor: Samsung Co driver: ipu3-cio2 bus ID: 00:14.3 
  Device-3: Intel Sunrise Point-LP HD Audio vendor: Samsung Co 
  driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
  Sound Server: ALSA v: k5.4.0-33-generic 
Network:
  Device-1: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter 
  vendor: Samsung Co driver: ath10k_pci v: kernel port: f040 bus ID: 01:00.0 
  IF: wlp1s0 state: down mac: <filter> 
  Device-2: Qualcomm Atheros type: USB driver: btusb bus ID: 1-3:2 
  Device-3: ASIX AX88179 Gigabit Ethernet type: USB driver: ax88179_178a 
  bus ID: 1-4.2.2:7 
  IF: enx00909e9dd80e state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 238.47 GiB used: 8.32 GiB (3.5%) 
  ID-1: /dev/sda vendor: Samsung model: MZNLN256HMHQ-000 size: 238.47 GiB 
  temp: 25 C 
Partition:
  ID-1: / size: 167.94 GiB used: 8.29 GiB (4.9%) fs: ext4 dev: /dev/sda7 
Sensors:
  System Temperatures: cpu: 36.0 C mobo: 31.0 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 215 Uptime: 15m Memory: 7.68 GiB used: 1.45 GiB (18.9%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.16 
  inxi: 3.0.38 


aplay -l

*** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC298 Analog [ALC298 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by P-I H on 2020-06-05
Have you used alsamixer to check if volumes are OK and nothing is mute.
You use F6 to select sound cards

---

### Post by Yellow Pasque on 2020-06-05
Googling around, I see a lot of complaints of no sound on Samsung devices with ALC298 codec. Launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1834566](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1834566)

---


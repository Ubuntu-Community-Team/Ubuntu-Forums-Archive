---
title: "microphone not working"
date: 2020-04-06
forum: Hardware
---

### Post by alex-coqueiro on 2020-04-06
my mic is not working, could anyone help! Thanks!

[B]inxi -Fxxxrz

[/B]```
System:
  Host: home Kernel: 5.3.0-45-generic x86_64 bits: 64 compiler: gcc v: 9.2.1 
  Desktop: Gnome 3.34.3 wm: gnome-shell dm: GDM3 3.34.1 
  Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:
  Type: Desktop Mobo: Micro-Star model: A320M PRO-VH PLUS(MS-7B07) v: 1.0 
  serial: <filter> UEFI: American Megatrends v: 3.E0 date: 01/22/2019 
CPU:
  Topology: Quad Core model: AMD Ryzen 5 1500X bits: 64 type: MT MCP 
  arch: Zen rev: 1 L2 cache: 2048 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 55997 
  Speed: 1377 MHz min/max: 1550/3500 MHz boost: enabled Core speeds (MHz): 
  1: 1376 2: 1377 3: 1376 4: 1377 5: 1377 6: 1379 7: 1377 8: 1454 
Graphics:
  Device-1: NVIDIA GP102 [GeForce GTX 1080 Ti] vendor: Gigabyte 
  driver: nvidia v: 435.21 bus ID: 1f:00.0 chip ID: 10de:1b06 
  Display: x11 server: X.Org 1.20.5 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa compositor: gnome-shell 
  resolution: 1920x1080~144Hz 
  OpenGL: renderer: GeForce GTX 1080 Ti/PCIe/SSE2 v: 4.6.0 NVIDIA 435.21 
  direct render: Yes 
Audio:
  Device-1: NVIDIA GP102 HDMI Audio vendor: Gigabyte driver: snd_hda_intel 
  v: kernel bus ID: 1f:00.1 chip ID: 10de:10ef 
  Device-2: AMD Family 17h HD Audio vendor: Micro-Star MSI 
  driver: snd_hda_intel v: kernel bus ID: 21:00.3 chip ID: 1022:1457 
  Sound Server: ALSA v: k5.3.0-45-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Micro-Star MSI driver: r8169 v: kernel port: f000 bus ID: 1b:00.0 
  chip ID: 10ec:8168 
  IF: enp27s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 1.36 TiB used: 145.75 GiB (10.5%) 
  ID-1: /dev/sda vendor: Seagate model: ST1000DM010-2EP102 size: 931.51 GiB 
  speed: 6.0 Gb/s rotation: 7200 rpm serial: <filter> rev: CC43 scheme: GPT 
  ID-2: /dev/sdb vendor: SanDisk model: SDSSDHP256G size: 238.47 GiB 
  speed: 6.0 Gb/s serial: <filter> rev: 6RL scheme: GPT 
  ID-3: /dev/sdc vendor: SanDisk model: SSD PLUS 240 GB size: 223.58 GiB 
  speed: 6.0 Gb/s serial: <filter> rev: 00RL scheme: MBR 
Partition:
  ID-1: / size: 200.73 GiB used: 145.72 GiB (72.6%) fs: ext4 dev: /dev/sdc1 
  ID-2: swap-1 size: 18.62 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sdc5 
Sensors:
  System Temperatures: cpu: 44.9 C mobo: N/A gpu: nvidia temp: 58 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 30% 
Repos:
  Active apt repos in: /etc/apt/sources.list 
  1: deb http://br.archive.ubuntu.com/ubuntu/ eoan main restricted
  2: deb http://br.archive.ubuntu.com/ubuntu/ eoan-updates main restricted
  3: deb http://br.archive.ubuntu.com/ubuntu/ eoan universe
  4: deb http://br.archive.ubuntu.com/ubuntu/ eoan-updates universe
  5: deb http://br.archive.ubuntu.com/ubuntu/ eoan multiverse
  6: deb http://br.archive.ubuntu.com/ubuntu/ eoan-updates multiverse
  7: deb http://br.archive.ubuntu.com/ubuntu/ eoan-backports main restricted universe multiverse
  8: deb http://security.ubuntu.com/ubuntu eoan-security main restricted
  9: deb http://security.ubuntu.com/ubuntu eoan-security universe
  10: deb http://security.ubuntu.com/ubuntu eoan-security multiverse
  11: deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
  Active apt repos in: /etc/apt/sources.list.d/google-chrome.list 
  1: deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
  Active apt repos in: /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-eoan.list 
  1: deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu eoan main
  Active apt repos in: /etc/apt/sources.list.d/lutris-team-ubuntu-lutris-eoan.list 
  1: deb http://ppa.launchpad.net/lutris-team/lutris/ubuntu eoan main
  Active apt repos in: /etc/apt/sources.list.d/steam.list 
  1: deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
  2: deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
Info:
  Processes: 342 Uptime: 23m Memory: 15.65 GiB used: 4.14 GiB (26.5%) 
  Init: systemd v: 242 runlevel: 5 Compilers: gcc: 9.2.1 alt: 9 Shell: bash 
  v: 5.0.3 running in: gnome-terminal inxi: 3.0.36
```
[B]
[B]aplay -l

[/B][/B]```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```[B][B]

[B]tail /etc/modprobe.d/alsa-base.conf

[/B][/B][/B]```
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=alc255-acer
options snd-hda-intel model=dell-headset-multi
options snd-hda-intel model=headset-mic
```

---

### Post by TheFu on 2020-04-06
In pavcontrol, the far right tab, verify that the headset device is set to "duplex". Disable any audio devices you won't use immediately. Turn them "off" in pavcontrol.  i usually disable any devices that won't be used (set them off) to prevent different programs from getting confused.

Next, work from right to left in the other tabs to ensure the levels are set for the correct device, correct level, and not muted.  When you talk, the levels for any active mic should move up and down.  if not, check it isnt' muted and is the only mic enabled.

Pulse tries to connect the latest device up, so sometimes after doing all of that, i'll unplug then re-plug the headset back in. That always fixes it provided I&#8217;ve disabled other devices already.

---


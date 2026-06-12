---
title: "nvidia driver stopped loading, nouveau loads instead"
date: 2021-08-16
forum: Hardware
---

### Post by Wise Ferret on 2021-08-16
I have gtx770 on ubuntu 21.04. My nvidia driver stopped loading, nouveau loads instead.

This is my hardware:

```
$ inxi -Fxz
System:
  Kernel: 5.11.0-31-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 
  Desktop: GNOME 3.38.4 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Desktop System: ASUS product: All Series v: N/A serial: <filter> 
  Mobo: ASUSTeK model: H87M-E v: Rev X.0x serial: <filter> 
  BIOS: American Megatrends v: 0904 date: 01/06/2014 
CPU:
  Info: Quad Core model: Intel Core i5-4570 bits: 64 type: MCP arch: Haswell 
  rev: 3 L2 cache: 6 MiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 25541 
  Speed: 3421 MHz min/max: 800/3600 MHz Core speeds (MHz): 1: 3421 2: 3482 
  3: 3489 4: 3450 
Graphics:
  Device-1: NVIDIA GK104 [GeForce GTX 770] vendor: Gigabyte driver: nouveau 
  v: kernel bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.11 driver: loaded: modesetting 
  unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: NVE4 v: 4.3 Mesa 21.0.3 direct render: Yes 
Audio:
  Device-1: Intel 8 Series/C220 Series High Definition Audio vendor: ASUSTeK 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Device-2: NVIDIA GK104 HDMI Audio vendor: Gigabyte driver: snd_hda_intel 
  v: kernel bus ID: 01:00.1 
  Device-3: Logitech Headset H340 type: USB 
  driver: hid-generic,snd-usb-audio,usbhid bus ID: 3-11:4 
  Sound Server: ALSA v: k5.11.0-31-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: ASUSTeK H81M-C driver: r8169 v: kernel port: d000 bus ID: 03:00.0 
  IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
  Device-2: Ralink RT5392 PCIe Wireless Network Adapter 
  vendor: D-Link System driver: rt2800pci v: 2.3.0 port: d000 
  bus ID: 04:00.0 
  IF: wlp4s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 931.51 GiB used: 414.97 GiB (44.5%) 
  ID-1: /dev/sda vendor: Western Digital model: WD1003FZEX-00MK2A0 
  size: 931.51 GiB 
Partition:
  ID-1: / size: 454.04 GiB used: 414.97 GiB (91.4%) fs: ext4 dev: /dev/sda6 
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 1.8 MiB (0.1%) file: /swapfile 
Sensors:
  System Temperatures: cpu: 63.0 C mobo: 27.8 C gpu: nouveau temp: 43.0 C 
  Fan Speeds (RPM): N/A gpu: nouveau fan: 990 
Info:
  Processes: 281 Uptime: 3h 51m Memory: 7.71 GiB used: 4.41 GiB (57.3%) 
  Init: systemd runlevel: 5 Compilers: gcc: 10.3.0 Packages: 2811 
  Shell: Bash v: 5.1.4 inxi: 3.3.01
```

This is what journalctl has to say:

```
$ journalctl --grep="nvidia"
[...]
&#1488;&#1493;&#1490; 13 15:07:05 ape systemd-udevd[1659143]: nvidia: Process '/sbin/modprobe nvidia-modeset' failed with exit code 1.
&#1488;&#1493;&#1490; 13 15:07:06 ape kernel: nvidia-nvlink: Nvlink Core is being initialized, major device number 234
&#1488;&#1493;&#1490; 13 15:07:06 ape kernel: NVRM: The NVIDIA probe routine was not called for 1 device(s).
&#1488;&#1493;&#1490; 13 15:07:06 ape kernel: NVRM: This can occur when a driver such as: 
                               NVRM: nouveau, rivafb, nvidiafb or rivatv 
                               NVRM: was loaded and obtained ownership of the NVIDIA device(s).
&#1488;&#1493;&#1490; 13 15:07:06 ape kernel: NVRM: Try unloading the conflicting kernel module (and/or
                               NVRM: reconfigure your kernel without the conflicting
                               NVRM: driver(s)), then try loading the NVIDIA kernel module
                               NVRM: again.
&#1488;&#1493;&#1490; 13 15:07:06 ape kernel: NVRM: No NVIDIA devices probed.
[...more repetition of this]

```

This began only lately. What should I do to find the problem and resolve it? Is there more data I can supply to help?

---

### Post by Timothy Taylor on 2021-08-17
I had something similar a while back: after an update and restart, my system was locked in 640x480 graphics.  I selected the X.Org driver instead of NVIDIA and normal graphics were restored.

---

### Post by mastablasta on 2021-08-18
NVIDIA G**K**104 [COLOR=#000000][FONT=&quot][GeForce GTX 770][/FONT][/COLOR]

Kepler series is still supported.

Sometimes on kernel upgrade the driver does not get updated or does not patch the kernel correctly. so far it happened to me once. solution was to remove the driver and install it again. i am sur ethere is another solution but this was easiest one.

---

### Post by Wise Ferret on 2021-08-18
Thanks for the suggestions!
I solved my problem by blacklisting nouvaeu driver, as explained [here]("https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux").

---


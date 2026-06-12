---
title: "Question about graphics card"
date: 2023-11-10
forum: Hardware
---

### Post by markelfertig on 2023-11-10
My old HP that had an i5 processor couldn't handle the PS2 emulator without getting to hot.
However, the HP I just got, which also has an i5, must have a better graphics card as it can run the emultor in a safe range - it doesn't even break 60 degrees celsius.

Just a curious question - how can I check and see what graphics card is in this machine?

From the internet:
*Generally, anything between **40&#8211;65°C (or 104&#8211;149°F)** is considered a safe heat range for a normal workload. While running more intensive apps or games, the normal CPU temp range can increase to between 70&#8211;80°C (158&#8211;176°F). The rule of thumb is, a bad CPU temp is 80-85°C (176&#8211;185°F) or above*

---

### Post by Autodave on 2023-11-10
I believe that this command will tell you:   inxi -Fxxrzc0

---

### Post by markelfertig on 2023-11-10
> **Autodave said:**
> I believe that this command will tell you:   inxi -Fxxrzc0


Thanks so much for your help!

A lot of info is reported, using the command line you gave me, but tell me if this is a descent graphics card in my new machine - it has to be better than my older HP desktop that died (and would over heat when running PS2 emulator) - even though it had the same Intel i5 chip.

```

$ inxi -Fxxrzc0
System:
  Kernel: 6.2.0-36-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    tk: GTK 3.24.33 wm: gnome-shell dm: GDM3
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: HP product: HP EliteDesk 800 G3 SFF v: N/A
    serial: <superuser required> Chassis: type: 3 serial: <superuser required>
  Mobo: HP model: 8299 v: KBC Version 06.29 serial: <superuser required>
    UEFI: HP v: P01 Ver. 02.43 date: 07/28/2022
CPU:
  Info: quad core model: Intel Core i5-6500 bits: 64 type: MCP
    arch: Skylake-S rev: 3 cache: L1: 256 KiB L2: 1024 KiB L3: 6 MiB
  Speed (MHz): avg: 3414 high: 3495 min/max: 800/3600 cores: 1: 3495
    2: 3367 3: 3299 4: 3495 bogomips: 25599
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3
Graphics:
  Device-1: Intel HD Graphics 530 vendor: Hewlett-Packard driver: i915
    v: kernel ports: active: HDMI-A-1
    empty: DP-1, DP-2, DP-3, HDMI-A-2, HDMI-A-3 bus-ID: 00:02.0
    chip-ID: 8086:1912
  Device-2: Logitech Webcam C270 type: USB driver: snd-usb-audio,uvcvideo
    bus-ID: 1-10:6 chip-ID: 046d:0825
  Display: wayland server: X.org v: 1.21.1.4 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: i915 display-ID: 0
  Monitor-1: HDMI-A-1 model: HP 2009 res: 1600x900 dpi: 92
    diag: 509mm (20")
  OpenGL: renderer: Mesa Intel HD Graphics 530 (SKL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel 200 Series PCH HD Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:a2f0
  Device-2: Logitech Webcam C270 type: USB driver: snd-usb-audio,uvcvideo
    bus-ID: 1-10:6 chip-ID: 046d:0825
  Sound Server-1: ALSA v: k6.2.0-36-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Ethernet I219-LM vendor: Hewlett-Packard driver: e1000e
    v: kernel port: N/A bus-ID: 00:1f.6 chip-ID: 8086:15e3
  IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: tun0 state: unknown speed: 10000 Mbps duplex: full mac: N/A
Drives:
  Local Storage: total: 1.14 TiB used: 56.3 GiB (4.8%)
  ID-1: /dev/nvme0n1 vendor: Toshiba model: N/A size: 238.47 GiB
    speed: 31.6 Gb/s lanes: 4 serial: <filter> temp: 44.9 C
  ID-2: /dev/sda vendor: Samsung model: SSD 870 QVO 1TB size: 931.51 GiB
    speed: 6.0 Gb/s serial: <filter>
Partition:
  ID-1: / size: 915.32 GiB used: 56.29 GiB (6.1%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 210.5 MiB (10.3%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 52.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Repos:
  Packages: 2002 apt: 1984 snap: 18
  Active apt repos in: /etc/apt/sources.list
    1: deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy main restricted
    2: deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates main restricted
    3: deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy universe
    4: deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates universe
    5: deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy multiverse
    6: deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates multiverse
    7: deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-backports main restricted universe multiverse
    8: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security main restricted
    9: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security universe
    10: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security multiverse
  Active apt repos in: /etc/apt/sources.list.d/google-chrome.list
    1: deb [arch=amd64] [https://dl.google.com/linux/chrome/deb/](https://dl.google.com/linux/chrome/deb/) stable main
Info:
  Processes: 293 Uptime: 2h 4m Memory: 7.63 GiB used: 5.4 GiB (70.9%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: N/A Shell: Bash v: 5.1.16
  running-in: gnome-terminal inxi: 3.3.13

```

---

### Post by Yellow Pasque on 2023-11-10
> Intel HD Graphics 530 

Not the greatest gaming GPU in the word, but if you're running at 1600x900, it should be good enough if you don't insist on high quality settings in the more demanding games. 
Google "intel 530" if you want to see all the benchmarks/comparisons

> even though it had the same Intel i5 chip

Unless it was the exact same model number, it's not the same chip. Intel has now used 'i5' on a bunch of different CPU's.

---

### Post by markelfertig on 2023-11-10
> **Yellow Pasque said:**
> Not the greatest gaming GPU in the word, but if you're running at 1600x900, it should be good enough if you don't insist on high quality settings in the more demanding games. 
Google "intel 530" if you want to see all the benchmarks/comparisons



Unless it was the exact same model number, it's not the same chip. Intel has now used 'i5' on a bunch of different CPU's.


That's the thing about how Intel names their chips that I don't like.  They have multiple processors with the same chip, even though some are much better than the others.


Thanks for your reply!

---


---
title: "No sound with HP Laptop with AMD Ryzen 5 CPU"
date: 2023-10-14
forum: Hardware
---

### Post by nelly533 on 2023-10-14
On booting the sound once in 10 or so boot ups does work but after an update or reboot it does not again. I did install Pipewire but that made no difference so I just try not to reboot the laptop once it is working. Thanks for any help, 
inxi -Fxxz
System:
  Kernel: 6.2.0-34-generic x86_64 bits: 64 compiler: N/A Desktop: MATE 1.26.0
    wm: marco dm: LightDM Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: HP product: HP Laptop 15-ef2xxx v: N/A
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: HP model: 887A v: 59.23 serial: <superuser required> UEFI: AMI
    v: F.31 date: 08/02/2023
Battery:
  ID-1: BAT0 charge: 28.7 Wh (74.4%) condition: 38.6/38.6 Wh (100.0%)
    volts: 12.0 min: 11.3 model: HP Primary serial: <filter>
    status: Discharging
CPU:
  Info: 6-core model: AMD Ryzen 5 5500U with Radeon Graphics bits: 64
    type: MT MCP arch: Zen 2 rev: 1 cache: L1: 384 KiB L2: 3 MiB L3: 8 MiB
  Speed (MHz): avg: 1401 high: 1419 min/max: 1400/4056 boost: enabled
    cores: 1: 1397 2: 1400 3: 1400 4: 1400 5: 1400 6: 1400 7: 1400 8: 1400
    9: 1400 10: 1400 11: 1419 12: 1400 bogomips: 50304
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: AMD Lucienne vendor: Hewlett-Packard driver: amdgpu v: kernel
    pcie: speed: 8 GT/s lanes: 16 ports: active: eDP-1 empty: HDMI-A-1
    bus-ID: 03:00.0 chip-ID: 1002:164c
  Device-2: Quanta HP TrueVision HD Camera type: USB driver: uvcvideo
    bus-ID: 1-3:2 chip-ID: 0408:5365
  Display: x11 server: X.Org v: 1.21.1.4 compositor: marco v: 1.26.0
    driver: X: loaded: amdgpu,ati unloaded: fbdev,modesetting,vesa gpu: amdgpu
    display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1280x720 s-dpi: 96
  Monitor-1: eDP res: 1280x720 dpi: 95 diag: 395mm (15.5")
  OpenGL: renderer: RENOIR (renoir LLVM 15.0.7 DRM 3.49 6.2.0-34-generic)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: AMD Renoir Radeon High Definition Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel pcie: speed: 8 GT/s lanes: 16
    bus-ID: 03:00.1 chip-ID: 1002:1637
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    vendor: Hewlett-Packard driver: snd_rn_pci_acp3x v: kernel pcie:
    speed: 8 GT/s lanes: 16 bus-ID: 03:00.5 chip-ID: 1022:15e2
  Device-3: AMD Family 17h HD Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel pcie: speed: 8 GT/s lanes: 16
    bus-ID: 03:00.6 chip-ID: 1022:15e3
  Sound Server-1: ALSA v: k6.2.0-34-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: no
  Sound Server-3: PipeWire v: 0.3.79 running: yes
Network:
  Device-1: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter
    vendor: Hewlett-Packard driver: rtw_8821ce v: N/A pcie: speed: 2.5 GT/s
    lanes: 1 port: f000 bus-ID: 01:00.0 chip-ID: 10ec:c821
  IF: wlo1 state: up mac: <filter>
  IF-ID-1: tun0 state: unknown speed: 10000 Mbps duplex: full mac: N/A
Bluetooth:
  Device-1: Realtek Bluetooth Radio type: USB driver: btusb v: 0.8
    bus-ID: 1-4:8 chip-ID: 0bda:b00e
  Report: hciconfig ID: hci0 rfk-id: 69 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 238.47 GiB used: 17.24 GiB (7.2%)
  ID-1: /dev/nvme0n1 vendor: SK Hynix model: BC711 HFM256GD3JX013N
    size: 238.47 GiB speed: 31.6 Gb/s lanes: 4 serial: <filter> temp: 22.9 C
Partition:
  ID-1: / size: 45.53 GiB used: 16.36 GiB (35.9%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: partition size: 7.45 GiB used: 887 MiB (11.6%)
    priority: -2 dev: /dev/nvme0n1p3
Sensors:
  System Temperatures: cpu: 34.0 C mobo: N/A gpu: amdgpu temp: 33.0 C
  Fan Speeds (RPM): cpu: 0 fan-2: 0
Info:
  Processes: 554 Uptime: 4d 6h 59m Memory: 7.08 GiB used: 3.07 GiB (43.4%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: 11.4.0 alt: 11
  Packages: 2336 note: see --pkg apt: 2322 snap: 14 Shell: Bash v: 5.1.16
  running-in: mate-terminal inxi: 3.3.13

---


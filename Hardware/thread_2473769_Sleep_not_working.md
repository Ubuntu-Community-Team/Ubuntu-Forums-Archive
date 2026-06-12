---
title: "Sleep not working"
date: 2022-04-13
forum: Hardware
---

### Post by student-sfv on 2022-04-13
Hi,

I'm on Ubuntu 20.04.4 LTS, upgraded everything recently.
HW info:
```

$ inxi -Fxz
System:    Kernel: 5.13.0-39-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.9 
           Distro: Ubuntu 20.04.4 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: PRIME X570-P v: Rev X.0x serial: <filter> UEFI: American Megatrends v: 3001 
           date: 12/04/2020 
CPU:       Topology: 6-Core model: AMD Ryzen 5 3600X bits: 64 type: MT MCP arch: Zen L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 96005 
           Speed: 4000 MHz min/max: 2200/4000 MHz Core speeds (MHz): 1: 3996 2: 3998 3: 4000 4: 4000 5: 4000 6: 4000 7: 4000 
           8: 4000 9: 4000 10: 4000 11: 4000 12: 4000 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] vendor: ASUSTeK 
           driver: amdgpu v: kernel bus ID: 0b:00.0 
           Display: x11 server: X.Org 1.20.13 driver: ati,fbdev unloaded: modesetting,radeon,vesa resolution: 2560x1440~60Hz 
           OpenGL: renderer: AMD Radeon RX 5700 XT (NAVI10 DRM 3.41.0 5.13.0-39-generic LLVM 12.0.0) v: 4.6 Mesa 21.2.6 
           direct render: Yes 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel v: kernel bus ID: 0b:00.1 
           Device-2: Advanced Micro Devices [AMD] Starship/Matisse HD Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel 
           bus ID: 0d:00.4 
           Device-3: Kingston HyperX Virtual Surround Sound type: USB driver: hid-generic,snd-usb-audio,usbhid bus ID: 3-4:2 
           Sound Server: ALSA v: k5.13.0-39-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK driver: r8169 v: kernel port: f000 
           bus ID: 05:00.0 
           IF: enp5s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           Device-2: Microsoft XBOX ACC type: USB driver: mt76x2u bus ID: 1-5:3 
           IF: wlx6c5d3a070695 state: down mac: <filter> 
           Device-3: TP-Link 802.11ac NIC type: USB driver: usb-network bus ID: 5-3:2 
           IF-ID-1: br-1bed572afb4c state: up speed: 10000 Mbps duplex: unknown mac: <filter> 
           IF-ID-2: br-6f067f9eb05e state: down mac: <filter> 
           IF-ID-3: br-917f637b809e state: up speed: 10000 Mbps duplex: unknown mac: <filter> 
           IF-ID-4: br-a318eafb70ea state: down mac: <filter> 
           IF-ID-5: br-quacc-68904 state: down mac: <filter> 
           IF-ID-6: docker0 state: down mac: <filter> 
           IF-ID-7: docker_gwbridge state: up speed: 10000 Mbps duplex: unknown mac: <filter> 
           IF-ID-8: veth06062df state: up speed: 10000 Mbps duplex: full mac: <filter> 
           IF-ID-9: veth0f3d8ff state: up speed: 10000 Mbps duplex: full mac: <filter> 
           IF-ID-10: veth340ecc5 state: up speed: 10000 Mbps duplex: full mac: <filter> 
           IF-ID-11: vethd43714b state: up speed: 10000 Mbps duplex: full mac: <filter> 
           IF-ID-12: vethfb40ab5 state: up speed: 10000 Mbps duplex: full mac: <filter> 
           IF-ID-13: vethff92b5b state: up speed: 10000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 1.37 TiB used: 123.10 GiB (8.8%) 
           ID-1: /dev/nvme0n1 vendor: A-Data model: SX8200PNP size: 953.87 GiB 
           ID-2: /dev/nvme1n1 vendor: Intel model: SSDPEKNW010T9 size: 953.87 GiB 
           ID-3: /dev/sda vendor: Patriot model: Burst size: 447.13 GiB temp: 33 C 
Partition: ID-1: / size: 438.18 GiB used: 122.83 GiB (28.0%) fs: ext4 dev: /dev/dm-0 
           ID-2: /boot size: 922.0 MiB used: 247.5 MiB (26.8%) fs: ext4 dev: /dev/sda1 
Sensors:   System Temperatures: cpu: 52.8 C mobo: N/A gpu: amdgpu temp: 46 C 
           Fan Speeds (RPM): N/A gpu: amdgpu fan: 0 
Info:      Processes: 447 Uptime: 16m Memory: 15.54 GiB used: 5.01 GiB (32.2%) Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 
           Shell: bash v: 5.0.17 inxi: 3.0.38

```

Starting a few weeks ago, the sleep functionality has stopped working.
Previously I've had intermittent issues with the PC not coming back up after sleep sometimes, scenario like this:
[LIST]
[*]put PC to sleep
[*]fans/everything turns off
[*]press a key a while later
[*]fans turn back on but no image on monitor, no way to make it work other than reset button
[/LIST]
Now I've got a different behavior, not intermittent anymore, this one happens every time:
[LIST]
[*]put PC to sleep
[*]monitor turns off but fans do not
[*]cannot start it back up with any key presses, only way is with the reset button
[/LIST]

Can you help me figure out why this happens?

---


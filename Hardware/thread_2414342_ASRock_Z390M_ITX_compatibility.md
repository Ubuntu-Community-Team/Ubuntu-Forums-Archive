---
title: "ASRock Z390M ITX compatibility"
date: 2019-03-09
forum: Hardware
---

### Post by adrhc on 2019-03-09
Hi, please post here any experience you have with ASRock Z390M-ITX/ac from the point of view of hardware compatibility with Ubuntu. 

I specifically want to know:
1. what works out of box
2. what works but only with some tweaks applied (what tweaks?)
3. what doesn't work for the moment (e.g.: but a fix is to come in the future - which one?)
4. what doesn't work at all (and why)

---

### Post by him610 on 2019-03-09
While I don't have an ASRock Z390M-ITX/ac, I do have one of its predecessors, an H270M-ITX/ac, and I run Xubuntu 18.04.2 on it. It has been one of the better motherboards I have built systems around.

To address your questions:
1. what works out of box
Never any issues with drivers for components, devices, or peripherals. Every application I have attempted to run has run, so I suppose one could say everything works out of the box.

2. what works but only with some tweaks applied (what tweaks?)
Never found it necessary to tweak anything.

3. what doesn't work for the moment (e.g.: but a fix is to come in the future - which one?)
Refer to answers above.

4. what doesn't work at all (and why)
Refer to answers above.

My system configuration....
```

$ inxi -F
System:    Host: G4560 Kernel: 4.15.0-46-generic x86_64 bits: 64 Desktop: Xfce 4.12.3
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: desktop Mobo: ASRock model: H270M-ITX/ac serial: N/A
           UEFI: American Megatrends v: P2.50 date: 03/16/2018
CPU:       Dual core Intel Pentium G4560 (-MT-MCP-) cache: 3072 KB
           clock speeds: max: 3500 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz 4: 800 MHz
Graphics:  Card: NVIDIA GK104 [GeForce GTX 760]
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia Resolution: 2560x1080@59.98hz
           OpenGL: renderer: GeForce GTX 760/PCIe/SSE2 version: 4.6.0 NVIDIA 390.116
Audio:     Card-1 Intel 200 Series PCH HD Audio driver: snd_hda_intel
           Card-2 NVIDIA GK104 HDMI Audio Controller driver: snd_hda_intel
           Card-3 Logitech Webcam B500 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-46-generic
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           IF: enp0s31f6 state: up speed: 100 Mbps duplex: full mac: 70:85:c2:3b:46:xx
           Card-2: Intel I211 Gigabit Network Connection driver: igb
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: 70:85:c2:3b:46:xx
           Card-3: Intel Wireless 3160 driver: iwlwifi
           IF: wlp4s0 state: up mac: f4:06:69:f1:17:xx
Drives:    HDD Total Size: 1000.2GB (8.3% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 250.1GB
           ID-2: /dev/sdb model: ST9750420AS size: 750.2GB
Partition: ID-1: / size: 228G used: 11G (5%) fs: ext4 dev: /dev/sda2
           ID-2: /home size: 599G used: 67G (12%) fs: ext4 dev: /dev/sdb1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 31.0C mobo: N/A gpu: 32C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 262 Uptime: 2:03 Memory: 2003.6/7942.2MB Client: Shell (bash) inxi: 2.3.56 

$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 05)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 05)
00:14.0 USB controller: Intel Corporation 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller
00:14.2 Signal processing controller: Intel Corporation 200 Series PCH Thermal Subsystem
00:16.0 Communication controller: Intel Corporation 200 Series PCH CSME HECI #1
00:17.0 SATA controller: Intel Corporation 200 Series PCH SATA controller [AHCI mode]
00:1c.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #3 (rev f0)
00:1c.5 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #6 (rev f0)
00:1c.6 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #7 (rev f0)
00:1d.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #9 (rev f0)
00:1f.0 ISA bridge: Intel Corporation 200 Series PCH LPC Controller (H270)
00:1f.2 Memory controller: Intel Corporation 200 Series/Z370 Chipset Family Power Management Controller
00:1f.3 Audio device: Intel Corporation 200 Series PCH HD Audio
00:1f.4 SMBus: Intel Corporation 200 Series/Z370 Chipset Family SMBus Controller
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 760] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
03:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
04:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)

$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 001 Device 003: ID 2001:f103 D-Link Corp. DUB-H7 7-port USB 2.0 hub
Bus 001 Device 006: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 001 Device 002: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

By the way, I do not play games nor do I dual-boot. Xubuntu is the only OS/distro that has ever been installed on this machine. It is housed in a CoolerMaster Elite 130 case with a EVGA 550 B3  PSU.

---

### Post by oldfred on 2019-03-09
Some systems and I have seen older Asrock have issues with Asmedia ports. You just cannot use them.              
 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564) 
      
All systems need UEFI update and regular monitoring on vendor updating UEFI. This is for Meltdown/Spectre        vulnerabilities. Both Windows & Ubuntu have updates for those, but UEFI also needs updates. All vendors also are updating for other fixes also.

---

### Post by adrhc on 2019-03-10
Hi guys, while I appreciate the experience with the previous models I just want to point that this board supports 8th and 9th generation intel CPUs which I suspect might pose incompatibility issues (at least momentarily).

---

### Post by radams2k on 2019-08-22
I may be a bit late here, but ...

I'm running Debian 10/Buster (the latest version) on this motherboard, paired with the Intel Core i7 8700. Mine was a very routine installation - nothing weird or unusual. I completed my build a few weeks ago and everything works perfectly - no tweaking, no extra packages or modules to install / enable / blacklist, no headaches - everything worked straight-away.

I would imagine that the latest, stable, version of Ubuntu will yield similar results.

Good luck!!!

---


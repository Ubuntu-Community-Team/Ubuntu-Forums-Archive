---
title: "MSI P67A-C45 B3 : compatible or not?"
date: 2012-01-05
forum: Hardware
---

### Post by PileOuFace on 2012-01-05
Hello,

I plan to buy a new desktop computer and I would like to be sure everything works fine on Ubuntu (network, sound...)  :)

- motherboard => MSI P67A-C45 B3 (CPU Intel Sandybridge, Intel P67 Express, 1155 Socket)
- CPU : Intel Core i5-2500K - Quad Core
- ASUS GeForce GTX 560 Ti 1 GB

I think it should work fine but I would appreciate if anyone could provide a feed back or comment before I order this motherboard.

Many thanks for your help  ):P

---

### Post by dj.houba on 2012-01-05
Hi,
I don't know, if it will be same, but I have MSI P67A-GD65 with i5 2500k and everything is OK. Network, sound -> working.
I had problem with freezes, but it was due to old GPU drivers. I manually instaled the newest drivers for GPU and everything is perfect now.

---

### Post by dj.houba on 2012-01-05
And can you do something for me? I'm thinking about new graphic card. I'm trying to decide between AMD HD 6950 or nVidia GTX 560Ti.

1) After you will buy it and test it can you write me some review here?

2)Why you decided to buy nVidia - do you have some interesting links about it?

Thank you

---

### Post by PileOuFace on 2012-01-05
> **dj.houba said:**
> 
1) After you will buy it and test it can you write me some review here?

Ok, I will do it if I select this card.

> **dj.houba said:**
> 
2)Why you decided to buy nVidia - do you have some interesting links about it?

I might be wrong, I think the Linux drivers provided by Nvidia are better than the ones provided by ATI. I am not sure if the ATI drivers for Linux are really stable because few years ago, many Linux users experienced problems with the ATI cards. But maybe ATI improved their drivers, now.

---

### Post by dj.houba on 2012-01-05
> **PileOuFace said:**
> I might be wrong, I think the Linux drivers provided by Nvidia are better than the ones provided by ATI. I am not sure if the ATI drivers for Linux are really stable because few years ago, many Linux users experienced problems with the ATI cards. But maybe ATI improved their drivers, now.

I wrote something about it: [http://ubuntuforums.org/showthread.php?t=1904620](http://ubuntuforums.org/showthread.php?t=1904620)

---

### Post by Basher101 on 2012-01-05
my board uses the Z68 chipset (see full specs below) but everything is absoluteley fine...i only had some issues with the GTX 570, i had blackscreen on the tty1 consoles (it was fixed by changing something with the Initramfs). otherwise i have yet to find something that does not work..

---

### Post by HilbertPeter on 2012-01-06
I don't think so that ubuntu is compatible with every software and laptop. It require some different configuration.

[patent attorney]("http://www.patentsusa.com")

---

### Post by PileOuFace on 2012-01-06
Thanks for all your answers, I think I am going to buy this motherboard or maybe a MSI P67A-GD65 (cheaper).

I will provide a feedback in few days :)

---

### Post by PileOuFace on 2012-01-24
Hi All,

I finally bought this [computer]("http://www.ldlc.com/fiche/PB00110771.html") (Motherboard    MSI P67A-C45) and I installed Ubuntu 11.10.
So far, no problem :
- sound : ok
- wired network : ok
- suspend function : ok
- Hibernation : ok
- 3D : ok
- CPU frequency management : ok

**lsusb** : 
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```**lspci**
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF110 [GeForce GTX 560 Ti] (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0e0c (rev a1)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
04:00.0 PCI bridge: ASMedia Technology Inc. Device 1080 (rev 01)
06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
08:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (rev 01)
```**lscpu**
```
Architecture:          x86_64
mode(s) opératoire(s) des microprocesseurs :32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) par c&#339;ur : 1
C&#339;ur(s) par socket : 4
Socket(s) de microprocesseur :1
N&#339;ud(s) NUMA :       1
Identifiant constructeur :GenuineIntel
Famille de microprocesseur :6
Modèle :             42
Version :             7
Vitesse du microprocesseur en MHz :1600.000 (<= note : au repos)
BogoMIPS:              6583.80
Virtualisation :      VT-x
cache L1d :           32K
cache L1i :           32K
cache L2 :            256K
cache L3 :            6144K
NUMA node0 CPU(s):     0-3

```I ran 3 benchmarks :[Unigine Heaven]("http://unigine.com/products/heaven/") (resolution 1920x1080)

Here are the options I used : 

Render:    opengl
Mode:    1920x1080 fullscreen
Shaders:    high
Textures:    high
Filter:    trilinear
Anisotropy:    16x
Occlusion:    enabled
Refraction:    enabled
Volumetric:    enabled
Tessellation:    extreme

1) Unity 3D => x64_1920x1080_fullscreen_tess_extreme
Heaven Benchmark v2.5 Basic
FPS: 29.7
Scores: 748
Min FPS: 12.4
Max FPS: 68.8

2) Unity 2D => x64_1920x1080_fullscreen_tess_extreme
Heaven Benchmark v2.5 Basic
FPS:    29.9
Scores:    754
Min FPS:    12.4
Max FPS:    70.0

3) Unity 2D, antialiasing 4x => x64_1920x1080_fullscreen_tess_extreme
FPS:     24.7
Scores: 623
Min FPS:    11.6
Max FPS:    53.0

For information, here is the [detailed configuration]("http://www.hardware.fr/articles/786-5/guide-pc-hardware-fr.html")n :
- NZXT Source 210 Elite Noir    
Alimentation    Corsair CX500 V2    
Motherboard    MSI P67A-C45    
CPU    Intel Core i5-2500K    
Cooler :   Cooler Master Hyper 212 EVO    
M emory  G.Skill XL Series RipJaws X Series 2x4 Go DDR3-1600 CL9    
3D video card :  ASUS GTX560 Ti DirectCUII 1 Go    
Hard Drive :  Seagate 7200 12 1 To    
DVD    Samsung SH-222AB Noir

For moment, everything works fine, and Linux compatible :P

---


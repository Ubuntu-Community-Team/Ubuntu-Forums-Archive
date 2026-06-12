---
title: "C-Media CMI8738 with 5.1 &amp; mic"
date: 2017-06-27
forum: Hardware
---

### Post by xcore on 2017-06-27
hello, I have a problem which was discussed in this thread: [https://ubuntuforums.org/showthread.php?t=1402144](https://ubuntuforums.org/showthread.php?t=1402144),
but the tread is outdated and the given solutions dont seem to work on ubuntu 16.04, especially since the thread was about a problem with mint.

what i figured out :
[LIST]
[*]my sound card works fine with either 5.1 surround or stereo + mic. 
[*][https://ubuntuforums.org/member.php?u=566591](https://ubuntuforums.org/member.php?u=566591) (Markbuntu) said that its not possible on his sound-card, but mine has connectors for rearLR, center+sub and frontLR PLUS mic and line in. so it should work i think. 
[/LIST]

if you need the information:
lukas@lukas-rechner:~$ lspci
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Complex
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1425
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 5
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 950] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
02:05.0 Multimedia audio controller: C-Media Electronics Inc CMI8738/CMI8768 PCI Audio (rev 10)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
lukas@lukas-rechner:~$
``` 
lukas@lukas-rechner:~$ lsusb
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 062a:4101 Creative Labs Wireless Keyboard/Mouse
Bus 005 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lukas@lukas-rechner:~$ 
```
lukas@lukas-rechner:~$ cat /proc/asound/cards
```
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe200000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe080000 irq 37
 2 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xd000, irq 20
lukas@lukas-rechner:~$
``` 
lukas@lukas-rechner:~$ cat /proc/asound/modules
```
 0 snd_hda_intel
 1 snd_hda_intel
 2 snd_cmipci
lukas@lukas-rechner:~$ 
lukas@lukas-rechner:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Generic [HD-Audio Generic], Gerät 0: ALC887-VD Analog [ALC887-VD Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: Generic [HD-Audio Generic], Gerät 3: ALC887-VD Digital [ALC887-VD Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 7: HDMI 1 [HDMI 1]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 8: HDMI 2 [HDMI 2]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 9: HDMI 3 [HDMI 3]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 2: CMI8738 [C-Media CMI8738], Gerät 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 2: CMI8738 [C-Media CMI8738], Gerät 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 2: CMI8738 [C-Media CMI8738], Gerät 2: CMI8738-MC6 [C-Media PCI IEC958]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
lukas@lukas-rechner:~$
``` 
lukas@lukas-rechner:~$ arecord -l
```
**** Liste der Hardware-Geräte (CAPTURE) ****
Karte 0: Generic [HD-Audio Generic], Gerät 0: ALC887-VD Analog [ALC887-VD Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: Generic [HD-Audio Generic], Gerät 2: ALC887-VD Alt Analog [ALC887-VD Alt Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 2: CMI8738 [C-Media CMI8738], Gerät 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 2: CMI8738 [C-Media CMI8738], Gerät 2: CMI8738-MC6 [C-Media PCI IEC958]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
```

---


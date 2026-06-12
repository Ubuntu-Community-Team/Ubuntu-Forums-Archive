---
title: "Corsair VOID gaming headset causes apps to hang."
date: 2016-02-08
forum: Hardware
---

### Post by 1clue on 2016-02-08
Hi,

I bought a Corsair VOID RGB USB gaming headset a few weeks ago.  Everything works out-of-the-box, sound is on par with what I paid for it, but there's a problem I didn't really relate to the headset right away.

Every now and then, whether I change anything on the headset itself or not, certain parts of my system hang.  
[LIST=1]
[*]I can't get to the sound widget in the upper right or any of the other widgets up there
[*]I very often can't get to apps that use sound, e.g. Firefox, a music player, etc.
[*]This is sometimes related to operating the on-headset controls:
[LIST=1]
[*]Raise/lower the microphone boom.
[*]Mute/unmute the microphone via the headset button.
[*]Volume control thumbwheel manipulation.
[/LIST]

[*]Sometimes it just happens, and I am 100% positive that I didn't use any sound-related control.
[*]About 80% of the time, I can unplug the USB headset and I get responsiveness for the sound control panel and maybe the audio app.
[/LIST]

Side notes:
[LIST=1]
[*]I had a Logitech USB gaming headset before, it worked fine with no problems.  I broke it, went without for a few weeks and then bought the Corsair.
[*]Sometimes firefox hangs anyway even before my old headset broke, especially after a sleep or using a media-rich site like CNN or Bloomberg or YouTube or Facebook.  If this happens I need to killall firefox in order to get things back, I can't close the app using any GUI tool I can reach.  I kill it, restart it immediately and it seems normal.  This is new but older than any headset issues.
[/LIST]

The firefox hanging was there before I got the headset, it was/is annoying but not affecting business.  If somebody knows the answer I'll gladly listen, but really this thread is about the USB headset.

The USB headset is a huge pain, since it also affects communication with my coworkers and customers.

Does anyone have any ideas?  I'm using stock Ubuntu 15.04, very little change with respect to eye candy.  This is a development machine, not a recreational toy.

```

$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 003: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 010 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 008: ID 1b1c:1b2a Corsair 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 174c:5106 ASMedia Technology Inc. Transcend StoreJet 25M3
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 PCI bridge: PLX Technology, Inc. PEX 8509 8-lane, 8-port PCI Express Switch (rev aa)
02:01.0 PCI bridge: PLX Technology, Inc. PEX 8509 8-lane, 8-port PCI Express Switch (rev aa)
02:02.0 PCI bridge: PLX Technology, Inc. PEX 8509 8-lane, 8-port PCI Express Switch (rev aa)
02:03.0 PCI bridge: PLX Technology, Inc. PEX 8509 8-lane, 8-port PCI Express Switch (rev aa)
02:04.0 PCI bridge: PLX Technology, Inc. PEX 8509 8-lane, 8-port PCI Express Switch (rev aa)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
07:00.0 VGA compatible controller: NVIDIA Corporation GT200 [GeForce GTX 260] (rev a1)
08:00.0 PCI bridge: Pericom Semiconductor Device 2304 (rev 05)
09:01.0 PCI bridge: Pericom Semiconductor Device 2304 (rev 05)
09:02.0 PCI bridge: Pericom Semiconductor Device 2304 (rev 05)
0a:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
0b:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
0c:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
0c:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
0d:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
10:00.0 Multimedia audio controller: Creative Labs SB X-Fi
ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)

```

```

$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 26
Model name:            Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
Stepping:              5
CPU MHz:               1600.000
CPU max MHz:           2668.0000
CPU min MHz:           1600.0000
BogoMIPS:              5345.62
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K
NUMA node0 CPU(s):     0-7

```

---

### Post by Glenn_B._Jakobsen on 2016-03-28
Did you figure this one out? I'm sitting in the exact same boat.

---

### Post by 1clue on 2016-03-28
No.

I found that unplugging the headset, waiting a few seconds and then plugging it back in usually brings it back.

I made a script to set my preferred sound card and then set up a hot key for that.

Not a solution but a semi-satisfactory work-around until I figure it out.

[I]**Edit:** I guess you'll be wanting the script next.
```

pacmd set-default-source alsa_input.usb-Cosair_Corsair_VOID_RGB_USB_Gaming_Headset_00000000-00.iec958-stereo
pacmd set-default-sink alsa_output.usb-Cosair_Corsair_VOID_RGB_USB_Gaming_Headset_00000000-00.iec958-stereo

```
[/I]

---

### Post by Glenn_B._Jakobsen on 2016-03-28
Okay I found a fix and did a small write up for our specific case, hope it helps you.

Don't know if it's OK to link to my blog, but here goes: [http://www.c0urier.net/2016/corsair-gaming-void-usb-rgb-linux-fun](http://www.c0urier.net/2016/corsair-gaming-void-usb-rgb-linux-fun)

---

### Post by Glenn_B._Jakobsen on 2016-03-28
double posted. sorry.

---


---
title: "Mic is not working in E machine laptop"
date: 2011-07-21
forum: Hardware
---

### Post by SUPERFITTER on 2011-07-21
[FONT=Times New Roman][SIZE=3]My Mic is not working in E machine [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]laptop. I am using ubuntu version 11.04

I have this in amixer: 

dennis@dennis:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 60 [95%] [-4.50dB] [on]
  Front Right: Playback 59 [94%] [-6.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [on]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 16 [52%] [-10.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic2'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Input Source Select',0
  Capabilities: enum
  Items: 'Input1' 'Input2'
  Item0: 'Input1'
Simple mixer control 'Input Source Select',1
  Capabilities: enum
  Items: 'Input1' 'Input2'
  Item0: 'Input1'
dennis@dennis:~$ 

What should I do next? I have tried all the ideas that I could find in the different posts.
Thanks
[/SIZE][/FONT]

---

### Post by dougalkerr on 2011-07-21
You say you have tried all the ideas, here is one you may or may not have seen. I had a problem as well with an Acer One recently bought. It would pick up the mic, apparently but, we could hear no sound. For some reason when both channels for the mic are on there is no sound. When I knocked off one of the channels, hey presto, the mic was working again and out friends in Oz could talk with us once again.
Maybe, just maybe, it will work for you.

---

### Post by Volens on 2011-07-21
This could be way off, but I had issues with the mic on my laptop for a while too.
 
I was able to hear it through my speakers, but not record if I messed with the ALSAmixer.
 
My issue had to do with making sure alsa was using the right model setting for my card.
 
Here's the thread from my issue:
 
[http://ubuntuforums.org/showthread.php?t=1582088](http://ubuntuforums.org/showthread.php?t=1582088)
 
Dunno if it'll help you, but good luck.

---

### Post by SUPERFITTER on 2011-07-22
Not knowing what I'm doing does not help, but I found this:

dennis@dennis:~$ lspci -v

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
    Subsystem: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: d8000000-dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
    Subsystem: Rioworks Device 2032
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at ffe7f000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
    Memory window 0: 50000000-53fff000 (prefetchable)
    Memory window 1: 54000000-57fff000
    I/O window 0: 00003000-000030ff
    I/O window 1: 00003400-000034ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Askey Computer Corp. eMachines M6805 802.11g Built-in Wireless
    Flags: bus master, fast devsel, latency 64, IRQ 18
    Memory at d0000000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
    Subsystem: Rioworks Device 2032
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at 1c80 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
    Subsystem: Rioworks Device 2032
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at 1ca0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
    Subsystem: Rioworks Device 2032
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at 1cc0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
    Subsystem: Rioworks Device 2032
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at d0002800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
    Subsystem: VIA Technologies, Inc. VT8235 ISA Bridge
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro, via-ircc

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: Rioworks Device 2032
    Flags: bus master, medium devsel, latency 64, IRQ 23
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at 1ce0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
    Subsystem: Rioworks Device 2032
    Flags: medium devsel, IRQ 22
    I/O ports at 1000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
    Subsystem: Rioworks Device 2032
    Flags: medium devsel, IRQ 22
    I/O ports at 1400 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Modem
    Kernel modules: snd-via82xx-modem

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
    Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235
    Flags: bus master, medium devsel, latency 64, IRQ 23
    I/O ports at 1800 [size=256]
    Memory at d0002c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:13.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at d0002000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at 1c00 
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA controller])
    Subsystem: Rioworks Device 2032
    Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 16
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 2000 
    Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

dennis@dennis:~$ [FONT=Times New Roman][SIZE=256]

[/SIZE][/FONT]

---

### Post by Volens on 2011-07-22
OK,
 
Basically thats just a list of hardware detected by the kernel.
 
The part that would be of interest is this:
 
```

00:11.5 Multimedia **audio **controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
Subsystem: Rioworks Device 2032
Flags: medium devsel, IRQ 22
I/O ports at 1000 [size=256]
Capabilities: <access denied>
[B]Kernel driver in use: VIA 82xx Audio
Kernel modules: snd-via82xx
[/B]
```
 
I'll only be able to help you out if your problem ends up being like mine. I'll look into it and then try to explain what I did.

---

### Post by Volens on 2011-07-22
You are probably going to have to do some config file editing for ALSA.
 
Hit ALT + F2
 
and run:
 
```
gksudo gedit
```
 
open the file:
 
*/etc/modprobe.d/alsa-base.conf*
 
At the bottom of the file add:
 
```
options snd-via82xx position_fix=1
```
 
Restart your laptop, and see what that does.
 
If it makes it worse, take that line out and reboot again to get it back to where it was.
 
If this doesn't work, I don't have any other ideas.
 
And now for an explanation of whats going on (to the best of my ability). I don't know what you do and don't know so don't take this as condescension. Just trying to make it a learning experience if thats what you want.
 
Based on my experience a problem like this is due to the kernel (the base part of the OS that talks between hardware and software) loading the right module (pretty much a driver), but with the wrong option to accomodate your specific audio chip. So we are changing a config file (often found in /etc) to tell the kernel to load the module with an option.
 
Good Luck

---

### Post by SUPERFITTER on 2011-07-22
[FONT=Times New Roman][SIZE=4]Thank you Volens, this did not work for me. I will keep watching this thread to see if anyone else has any other ideas[/SIZE][/FONT].

[SIZE=4]Thanks again[/SIZE]

---

### Post by SUPERFITTER on 2011-07-23
[FONT=Times New Roman][SIZE=3]I installed Gnome Alsa Mixer and moved the horizontal slides to the right. Now I don't have any sound or mic in Skype, what should I do to correct this problem?[/SIZE][/FONT]

---


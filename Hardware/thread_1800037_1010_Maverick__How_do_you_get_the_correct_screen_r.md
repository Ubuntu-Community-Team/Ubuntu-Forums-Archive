---
title: "1010 Maverick  How do you get the correct screen resolution?"
date: 2011-07-08
forum: Hardware
---

### Post by eino1953 on 2011-07-08
I have had problems getting the correct screen resolutions.
This is the xorg.conf that I wrote That did not work.
Can someone tell me what I'm doing wrong? I'm at a complete loss.


Section "Monitor"
Identifier "Monitor0"
VendorName "Westinghouse"
ModelName "LD-325"
HorizSync 30.0 - 83.0
VertRefresh 50.0 - 76.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1366x768"
EndSubSection
EndSection

Here is the supported screen resolutions.

640X400 @ 85Hz
640X480 @ 60-75Hz
800X600 @ 56-60-75Hz
1024X768 @ 60-70-75-85Hz
1280X768 @ 60Hz
1360X768 @ 60Hz
1366@768 @ 60Hz
1440X900 @ 60Hz
As of now the only resolution that works is 800X600 @ 75Hz

Thank you in advance for your help.
Here is something else, That was forgotten when booting IRQ 12 is disabled. Could be a Hardware conflict .  I'll try disabling one piece of hardware at a time, to see what happens.

---

### Post by eino1953 on 2011-07-08
I didn't change any thing besides doing a cold boot. Now I'm having a screen orientation problem on the other screen resolutions. Including 600X800.

---

### Post by eino1953 on 2011-07-08
Help me please !!!

---

### Post by eino1953 on 2011-07-08
Bump

---

### Post by eino1953 on 2011-07-09
[SIZE=3][COLOR=Red]**I could use some input, or a link.**[/COLOR][/SIZE]  [SIZE=4][COLOR=Blue]**I have learned more about Linux and Ubuntu from reading, other material other than on the Ubuntu Forums. [COLOR=Red]I never got any answers to any [/COLOR]**[/COLOR][/SIZE]**[SIZE=4][COLOR=Red]Problems, or questions here!!!![/COLOR][/SIZE]**

---

### Post by westie457 on 2011-07-09
> **eino1953 said:**
> [SIZE=3][COLOR=Red]**I could use some input, or a link.**[/COLOR][/SIZE]  [SIZE=4][COLOR=Blue]**I have learned more about Linux and Ubuntu from reading, other material other than on the Ubuntu Forums. [COLOR=Red]I never got any answers to any [/COLOR]**[/COLOR][/SIZE]**[SIZE=4][COLOR=Red]Problems, or questions here!!!![/COLOR][/SIZE]**

You have now.

Try looking at this [http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

Also it is polite to wait 24 hours before bumping. None of us are getting paid to be here. We are here because we want to be.

---

### Post by eino1953 on 2011-07-09
Thanks for the link. I have tried that before. I'm still having a screen orientation problem .
I have an intergrated Intel 82865G in the system that's probably buggy.

---

### Post by eino1953 on 2011-07-09
This is what my system consists of :

lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
    Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02) (prog-if 00 [VGA controller])
    Subsystem: IBM Device [1014:0287]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
    Region 2: I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02) (prog-if 00 [UHCI])
    Subsystem: IBM Device [1014:0287]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02) (prog-if 00 [UHCI])
    Subsystem: IBM Device [1014:0287]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02) (prog-if 00 [UHCI])
    Subsystem: IBM Device [1014:0287]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02) (prog-if 00 [UHCI])
    Subsystem: IBM Device [1014:0287]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) (prog-if 20 [EHCI])
    Subsystem: IBM Device [1014:0287]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 23
    Region 0: Memory at e0080000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: e0100000-e01fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: IBM Device [1014:0287]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at 1810 [size=16]
    Region 5: Memory at 50000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
    Subsystem: IBM Device [1014:0287]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 9
    Region 4: I/O ports at 18a0 [size=32]
    Kernel modules: i2c-i801

03:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
    Subsystem: IBM Device [1014:0287]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 66 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at e0104000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at 2400 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

03:09.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 04)
    Subsystem: Creative Labs Device [1102:2006]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at 2440 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: EMU10K1_Audigy
    Kernel modules: snd-emu10k1

03:09.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 04)
    Subsystem: Creative Labs SB Audigy Game Port [1102:0040]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Region 0: I/O ports at 2480 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: Emu10k1_gameport
    Kernel modules: emu10k1-gp

03:09.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 04) (prog-if 10 [OHCI])
    Subsystem: Creative Labs SB Audigy FireWire Port [1102:0010]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 22
    Region 0: Memory at e0105000 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at e0100000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

03:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at 2000 [size=256]
    Region 1: Memory at e0105800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ndiswrapper
    Kernel modules: rtl8180
 [COLOR=Blue][SIZE=3]Hopefully someone can see something, I have over looked.[/SIZE][/COLOR]

---

### Post by westie457 on 2011-07-09
No idea if you have already seen this thread from early last year [http://ubuntuforums.org/archive/index.php/t-1400665.html](http://ubuntuforums.org/archive/index.php/t-1400665.html)

This is a bit drastic

It might have a workable solution for you once you have backed up your home folder including the hidden files hopefully to an external drive.
In the File Browser > Show hidden files or press ctrl+h.
select all then copy and paste to wherever you want to store them outside the Ubuntu partitions. 

Clean install to reset everything as new. Copy back to /home the hidden files a few at a time (preferably one at a time, that will take nearly forever though) until your display goes wrong. Once that has happened remove them one at a time working backwards - logging out and back in or rebooting as necessary - until your display is back to normal.

---

### Post by eino1953 on 2011-07-09
I have just upgraded to 11.4 natty. Now I'm back to default graphics now. How Do I get the correct 
**[SIZE=1]resolution for a monitor thats not automatically recognized.[/SIZE]**

[B][SIZE=1]11.4 only works under classic[/SIZE][SIZE=2]
[/SIZE][/B]

---

### Post by Blasphemist on 2011-07-09
Please see this page and run the following code from it. [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements) 
```
/usr/lib/nux/unity_support_test -p
```
Please post the results of that in quote tags. I doubt that you can run unity 3D. What may work best is to run this and install unity 2D. 
```
sudo apt-get install unity-2d
```

---

### Post by eino1953 on 2011-07-09
Here's the results of the support test.
> OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  1.3 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no


---

### Post by Blasphemist on 2011-07-09
I've see posts from many that very much like the unity 2D. Did you install that and try it yet? You have the i915 driver in use and I don't think you will improve on that.

---

### Post by eino1953 on 2011-07-09
I did install the 2d version. Now I need to get the setting, for the 32" LCD.
Here is the supported screen resolutions.

640X400 @ 85Hz
640X480 @ 60-75Hz
800X600 @ 56-60-75Hz
1024X768 @ 60-70-75-85Hz
1280X768 @ 60Hz
1360X768 @ 60Hz
1366@768 @ 60Hz
1440X900 @ 60Hz

With the default settings, I don't have the refresh rates, and the higher screen resolutions

---

### Post by Blasphemist on 2011-07-09
Here is a link that tells you how to do what you need. [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
```
xrandr --output VGA1 --mode 1440x900 --rate 60
```
Running this command in a terminal is the dynamic method, only good for that session, but it should help you verify that it works. You can implement it statically in xorg.conf. That is also shown on that link.

---


---
title: "SD Card not recognized"
date: 2010-12-06
forum: Hardware
---

### Post by mastermindg on 2010-12-06
I'm running 10.04 on a Gateway DX4300-22 desktop system. It's completely updated and has no other issues that I can see...

It's a 2GB SD (not SDHC) and it recognized immediately when I insert it with my usb thumb sd reader. There are no new lines ouputted in dmesg when the card is inserted into the front panel sd card slot. However, a light goes on that on the panel indicating that it has been recognized.

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c529 Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 1784:0008 TopSeed Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 018: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 003: ID 0a48:4001 I/O Interconnect 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 009: ID 0bb4:0c91 High Tech Computer Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller

```

---

### Post by dandnsmith on 2010-12-06
You cannot claim it is recognised, unless you can see the lines showing in in lspci or whatever - the light may be an automatic reaction to something plugged in and making some contacts.

Have you any evidence that that particular reader loaded with that particular card is read by any system?

It is quite possible to have incompatible readers, incompatible cards ...and of course dodgy usb ports.

---

### Post by mastermindg on 2010-12-06
> **dandnsmith said:**
> You cannot claim it is recognised, unless you can see the lines showing in in lspci or whatever
I am NOT claiming that it is recognized by Ubuntu(software)...hence the title.

> **dandnsmith said:**
> - the light may be an automatic reaction to something plugged in and making some contacts.
The system hardware is recognizing it...hence the light.

> **dandnsmith said:**
> 
Have you any evidence that that particular reader loaded with that particular card is read by any system?
The reader is internal and the reader isn't "read" by a system..it is recognized under lspci...which it is. The system was able to recognize the first SD card that I inserted into the sd reader...but nothing since. The remaining cards are readable by at least 3 other systems.

> **dandnsmith said:**
> It is quite possible to have incompatible readers, incompatible cards ...and of course dodgy usb ports.
USB ports are working fine..that's not my issue. The issue is with the SD reader which is located on the same interface: a front-panel with card readers, usb and mic inputs. I've ruled out incompatible cards...now I just need to determine if this is a hardware problem or a software problem.

---

### Post by mastermindg on 2010-12-06
Figured it out...

My issue is related to an already submitted bug report:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/504440]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/504440")

Everything is fine unless I choose "Safely Remove Drive" which actually removes the reader. Eject is the preferable method for internal readers. It unclear how this can be resolved as internal/external card readers are typically connected the same way (via usb). So for now...I'll just "Eject".

Thanks.

---

### Post by dandnsmith on 2010-12-07
I'm glad you've found the 'real' problem, and it's resolution.

What it boils down to is a misunderstanding of what the hardware really is, and how the OS interacts with it.

As you say, the card reader is a USB device (mounted tho' it is in a panel, obscuring the method of connection), so you have the same basic limitations as for a USB device, BUT with the added restriction that you are not physically able to unplug and replug the reader, so never getting the cue from the reader that there is hardware to be re-read.

It took my wife some time and a number of restatements of position before I got her to realise that you have to either eject the card, or reboot, in order to be able to 'talk' to the card reader again.

---


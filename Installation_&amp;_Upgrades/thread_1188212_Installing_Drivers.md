---
title: "Installing Drivers"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by prions on 2009-06-15
I'm trying to get some games work, so I booted up Envy to see my drivers. 

It says none of my drivers are supported nor installed. I have ATI and NVIDIA cards. 

How can I install them?

---

### Post by prions on 2009-06-15
Anything?

---

### Post by Mark Phelps on 2009-06-15
Standard rule of thumb in this forum is to bump no more often that once every 24 hours, so first off, quit bumping.

Second, need to know which specific model ATI and Nvidia cards you're planning on using because the drivers, especially for ATI, depend critically on the model of the card.  There is no single generic answer.

Finally, open source drivers are installed automatically; restricted drivers depend on the card models and the version of Ubuntu you're running.

---

### Post by prions on 2009-06-15
I'm totally new to Ubuntu and don't know where to view my drivers. I looked in system>administration>hardware drivers but it didn't show anything.

---

### Post by Amilo1718 on 2009-06-15
if everything works fine... why bother? :)

---

### Post by prions on 2009-06-15
I was trying to get Team Fortress 2 to work, but I would get a black screen after the valve splash.

So I assumed it was my drivers, I downloaded EnvyNg and it said that my drivers werent supported by Ubuntu. Nor could I see my drivers in the "Hardware Drivers" panel. 

So here I am. :o

---

### Post by suingi on 2009-06-16
I guess I have a driver problem too. A few days ago I reinstalled a computer with Ubuntu 8.10. It seems to work fine, but the computer is freezing every half hour or three quarters of an hour. 
Could this be a driver problem? and how do I fix it?
The machine does not turn off or go to sleep or anything in that direction. It just stops reacting.

Thanks for your help
Suingi

---

### Post by Mark Phelps on 2009-06-16
> **prions said:**
> I'm totally new to Ubuntu and don't know where to view my drivers. I looked in system>administration>hardware drivers but it didn't show anything.

We're not mind readers, here.  Can't help you with specifics without first knowing what model video card/chip you're using.

If you're running an ATI card/chip, entering "fglrxinfo" in a terminal will indicate whether or not you're running the ATI restricted drivers.

---

### Post by prions on 2009-06-16
```
buntu@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.4
```

---

### Post by Mark Phelps on 2009-06-16
OK, so you're not running the restricted ATI drivers.  Do an "lspci" in a terminal and look for information that will tell you which video chipset you're using.

---

### Post by prions on 2009-06-16
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller


```

:popcorn:

---

### Post by prions on 2009-06-17
Still not fixed.

---

### Post by prions on 2009-06-18
:|

---

### Post by Mark Phelps on 2009-06-18
Look in your lspci output where it says "VGA controller ..."

If you're running 9.04, you're stuck.  The open source drivers, which are installed by default, are all that are available.  AMD/ATI has dropped support for your chipset in the newer driver versions, and there is no driver version that works with Ubuntu 9.04.

---


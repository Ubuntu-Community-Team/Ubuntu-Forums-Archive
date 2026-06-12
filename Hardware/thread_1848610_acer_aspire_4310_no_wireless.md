---
title: "acer aspire 4310 no wireless"
date: 2011-09-22
forum: Hardware
---

### Post by reallush on 2011-09-22
hi guys, I'm pretty new to Ubuntu and i'm trying to set this up properly so I can use my laptop in a normal way.
but somehow.. the wireless just won't work.. I jacked in the internet cable and did an additional driver update and it properly updated the broadcom drivers.

but it still won't work or my windows orientated brain doesn't understand where to look.. because my router won't appear in the wifi menu in the taskbar and the wifi button also  doesn't go on when I press it..

please help, all other threads are ubuntu 10.04 and older... they're no use to me since I use the most recent one (11.04)

---

### Post by wolfen69 on 2011-09-22
Go back to Hardware Drivers to see which drivers were installed. (specific name) Then report back. You may need a different one.

---

### Post by reallush on 2011-09-23
Broadcom STA wireless driver
*tested by the Ubuntu Developers
License: propietary

This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

driver is activated and currently in use.

this was all I could get out of it I hope it is sufficient.

I also noticed that I didn't update the system so I'm doing it as Im typing now.

---

### Post by westie457 on 2011-09-23
Open a terminal (Ctrl+Alt+t) type ```
lspci -vnn
```
and then ```
rfkill list all
``` Highlight all the text and copy into a new reply pasting between [Code] tags by clicking the # in the menu bar.

Thank you.

---

### Post by reallush on 2011-09-23
```
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at dc240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d6000000-d7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: da000000-dbffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Memory behind bridge: dc000000-dc0fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at dc444400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d6000000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d8000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: wl, ssb

0a:06.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at dc000000 (32-bit, non-prefetchable) [size=4K]
	Memory at dc002000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

0a:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: bus master, slow devsel, latency 32, IRQ 22
	Memory at dc002800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0a:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:012f]
	Flags: slow devsel, IRQ 10
	Memory at dc001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

captainjacksparrow@ubuntu:~$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: acer-threeg: Wireless WAN
	Soft blocked: no
	Hard blocked: no
captainjacksparrow@ubuntu:~$
```

---

### Post by westie457 on 2011-09-23
Now your solution is here.

Remove the STA driver using Additional Drivers. **Do Not Reboot** just yet.
Open a terminal and run ```
sudo apt-get install b43-fwcutter

sudo apt-get firmware-b43-installer
```

Any errors you will have to enable some extra sources to get the firmware.

Once that has been installed remove the cable and reboot your system. Log in to your wireless and away you go.

---

### Post by reallush on 2011-09-23
```
captainjacksparrow@ubuntu:~$ sudo apt-get install b43-fwcutter
[sudo] password for captainjacksparrow: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
captainjacksparrow@ubuntu:~$ sudo apt-get firmware-b43-installer
E: Invalid operation firmware-b43-installer
captainjacksparrow@ubuntu:~$ 

```
somehow it doesn't want to do it... the first time it installed on the first code... but the second code it keeps telling that the operation is invalid.. 
also tried the code in 1 time in case you ment it like that but It didn't help either..  am I doing something wrong?


Please ignore this post for now.. my brain was malfunctioning.. I forgot to remove the driver first... I'll let you know when i'm done

---

### Post by reallush on 2011-09-23
```
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8-generic linux-headers-2.6.38-8 dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

interesting.. I guess... or I messed up somewhere..

---

### Post by reallush on 2011-09-23
I've done it!!! I got wireless to work now... 

I entered your code but somehow it didn't work.. so after dozens of trials I came up with another Idea..
I adjusted your code..
 
what I entered:
```
sudo apt-get install firmware-b43-installer
``` 

and that did the job for me... ^^ perhaps I'm gonna enjoy this stuff more then I thought... since i only have ubuntu installed for not even 24 hours..

thanks for all the help guys..

---

### Post by westie457 on 2011-09-23
> **reallush said:**
> I've done it!!! I got wireless to work now... 

I entered your code but somehow it didn't work.. so after dozens of trials I came up with another Idea..
I adjusted your code..
 
what I entered:
```
sudo apt-get install firmware-b43-installer
``` 

and that did the job for me... ^^ perhaps I'm gonna enjoy this stuff more then I thought... since i only have ubuntu installed for not even 24 hours..

thanks for all the help guys..

Glad its now working and I apologise for missing part of the command. Brain was fried at the time and I was running late for the drive to work.

Could you now mark this as solved please using Thread Tools at the top of the page.

Thank you.

---

### Post by diverselyrare on 2012-07-22
I also have the same problem for my Acer Aspire 4310. I tried your solution but it didn't work for me.

---

### Post by diverselyrare on 2012-07-22
> **reallush said:**
> I've done it!!! I got wireless to work now... 

I entered your code but somehow it didn't work.. so after dozens of trials I came up with another Idea..
I adjusted your code..
 
what I entered:
```
sudo apt-get install firmware-b43-installer
```and that did the job for me... ^^ perhaps I'm gonna enjoy this stuff more then I thought... since i only have ubuntu installed for not even 24 hours..

thanks for all the help guys..


It didn't work. :(

---

### Post by diverselyrare on 2012-07-22
```
cariel@ubuntu:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, fast devsel, latency 0
    Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at dc240000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d6000000-d7ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d8000000-d9ffffff
    Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: da000000-dbffffff
    Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    Memory behind bridge: dc000000-dc0fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 18d0 [size=8]
    I/O ports at 18c4 [size=4]
    I/O ports at 18c8 [size=8]
    I/O ports at 18c0 [size=4]
    I/O ports at 18b0 [size=16]
    Memory at dc444400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: medium devsel, IRQ 10
    I/O ports at 18e0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:011c]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d6000000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d8000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

0a:06.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02) (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at dc000000 (32-bit, non-prefetchable) [size=4K]
    Memory at dc002000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

0a:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02) (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: bus master, slow devsel, latency 32, IRQ 22
    Memory at dc002800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

0a:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:012f]
    Flags: slow devsel, IRQ 10
    Memory at dc001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

cariel@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by diverselyrare on 2012-07-22
Sorry for the disturbance. It actually worked! I'm sorry. :D

---

### Post by wildmanne39 on 2012-07-23
Old thread closed.

---


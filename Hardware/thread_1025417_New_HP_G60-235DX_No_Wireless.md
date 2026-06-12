---
title: "New HP G60-235DX No Wireless??"
date: 2008-12-30
forum: Hardware
---

### Post by c4bjenglacious on 2008-12-30
I just purchased a new laptop from best buy. I purchased a HP G60-235DX, When I first turned on the comp there was roughly 23gigs of vista and vista garbage. So the first thing I did is insert a Super Ubuntu 2008.11 disk and install to my hard drive. Everything went well until the blasted wireless Internet. Now this computer does not have a switch to turn on and off the wireless but it has a button. I have tried everything I can think of to get the wireless to work. I even looked into the bios to enable wireless all the time and there was nothing there. Thanks for any help

---

### Post by teaker1s on 2008-12-30
firstly I'm typing on debian not ubuntu, but you first want to look under System on desktop panel and locate 
System->Administration->Restricted Drivers/Hardware Drivers
see if there are any you can enable-if not you will need 
Applications>accessories>terminal

type these codes and post output

```
lsusb
```

```
lspci -v
```

post the outputs

---

### Post by c4bjenglacious on 2008-12-30
Ok I will look later tonight. I get off work late so I will post that information in the morning. Thanks for your help.

---

### Post by c4bjenglacious on 2009-01-01
lsusb output

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lspci -v output

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0
	Memory at d2500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 50e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 50c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 50a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at d4705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: d3700000-d46fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d14fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2600000-d36fffff
	Prefetchable memory behind bridge: 00000000d1500000-00000000d24fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 5040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at d4705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 221
	I/O ports at 5108 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 5100 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at d4705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: medium devsel, IRQ 11
	Memory at d4706000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: fast devsel, IRQ 11
	Memory at d4704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 220
	I/O ports at 3000 [size=256]
	Memory at d0410000 (64-bit, prefetchable) [size=4K]
	Memory at d0400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d0420000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: fast devsel, IRQ 17
	Memory at d2600000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci



I did enable a proprietary driver. "support for Atheros 802.11 wireless LAN cards" prior to making this post. The driver allows me to connect an Ethernet cable directly into the computer and connect to network/Internet. The problem is the wireless still will not work with this driver. I tried to install the windows driver using "windows wireless driver" in System>Admin>Windows Wireless Driver. Using this feature I can get the windows wireless driver application to find a driver it refers to as "netathr hardware present:yes. I do not know if I am on the right track. Thanks again for all your help.

---

### Post by punkybouy on 2009-01-01
I have a new G60 125 NR I bought from Best Buy.  The switch on the keyboard is not functional under Ubuntu but you can still set up wireless using the GUI app whose icon is up on the toolbar.  Check off the use wireless box and configure.  That's the good news.  The bad news is that current versions of Ubuntu will not come back from either a suspend or hibernate without cold booting (holding down the power switch for several seconds).  That was a deal killer for me so back came Vista.  I am however, sticking with Ubuntu on my other half a dozen boxes (one laptop and several desktops).  This one was an Xmas present for the GF.
I searched for a month for a fix to the suspend issue and found nothing. For some laptops suspend works just fine but not on the G60 I have.

---

### Post by c4bjenglacious on 2009-01-02
I have looked at the options up on the tool bar but when I left click on the icon there is only an option for wired connection. I have tried to manly set up a wireless connection and no work-eee. Should I disable the password for the "dlink wireless N" router? Would that help with my problem? I did have to install vista on another partition on my hd just so I can connect to wireless. I would love to go back to 100% Ubuntu but until I figure this out I cant. Thanks for your help. LINUX ROCKS!!! LOL

---

### Post by teaker1s on 2009-01-02
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html")

Above is for ibex8.10  not hardy lts8.04

---

### Post by punkybouy on 2009-01-02
I initially installed 8.04 and then struggled with the Atheros driver.  After a bit I installed 8.10 and it found the Atheros card right off the bat and allowed me to setup wireless.  Is it under System/Administration/Network where you enable wireless or add a wireless configuration?  I may also have used ndiswrapper and installed the Windows .inf file.  I can't remember for sure but I do think 8.10 64 bit found the wireless card right off the bat.

---

### Post by punkybouy on 2009-01-02
Still though, even if you get wireless working what good does it do if when you walk away from the laptop you come back and have to power off the machine and power it on which would eventually corrupt a file somewhere leaving you with a paper weight.

---

### Post by c4bjenglacious on 2009-01-03
teaker1s thank you so much. That fixed the problem. That was so easy. 



Thanks...

---

### Post by teaker1s on 2009-01-03
welcome:popcorn:

---

### Post by c4bjenglacious on 2009-01-03
is there anyway to create a startup program that would run all of the commands that I need to do to enable the wireless?

---

### Post by clayt0njknight on 2009-01-04
Mine works flawlessly.  It didn't out of the box, I had to go in and install the kernel-backports module.  After that I did the system update, restarted and the card was dead.  So I went into the restricted drivers applet (Hardware Drivers in 8.10) and disabled the standard atheros module and left the 5xxx module active.  Ibex runs awesome on this notebook, the only thing i'm struggling with now is the card reader.  But it didn't work in vista since I bought this thing so I'm wondering if it's just bad hardware.

---

### Post by c4bjenglacious on 2009-01-05
how do you install the kernel-backports module? I tried to get the drivers to "stick" but every time I turn off the comp I loose them. I tried another walk through on how to get the wireless to work. I did something jacked up and had to reinstall ubuntu back on my comp. I have a fresh install on there now. Where should I start. Thanks for your help.

---

### Post by c4bjenglacious on 2009-01-05
I apologize for posting my previous comment on the backport module. I am proud to make this post using wireless on my laptop. LOL. BOO YA!!!. Thanks everyone.


if anyone else is having problems with this this guy is a wild man with wireless. [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)


Thanks Again...

---


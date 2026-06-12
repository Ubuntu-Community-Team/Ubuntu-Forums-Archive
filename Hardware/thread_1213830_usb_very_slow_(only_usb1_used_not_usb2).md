---
title: "usb very slow (only usb1 used not usb2)"
date: 2009-07-15
forum: Hardware
---

### Post by macal94 on 2009-07-15
Hello all, I'm on jaunty.
Since my hardware upgrade with Asus P5QPL-VM EPU, using Intel G41 et ICH7.
My usb devices are only plugged on usb1 speed.

I've searched some help on forums, but for the moment I've no resolve my issue.

Please see the lsusb
maison@maison-desktop:~$ lsusb 
Bus 001 Device 007: ID 0dda:2026 Integrated Circuit Solution, Inc. USB2.0 Card Reader
Bus 001 Device 004: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c513 Logitech, Inc. MX3000 Cordless Desktop Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:8704 Hewlett-Packard deskjet 5900 series
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and maison@maison-desktop:~$ tail -100 /var/log/messages
Jul 14 13:59:40 maison-desktop kernel: [   11.592329] usb 1-4.1: reset full speed USB device using ehci_hcd and address 5
Jul 14 13:59:40 maison-desktop kernel: [   11.686986] scsi 4:0:0:0: Direct-Access     ICSI     IC1210        CF 1.6E PQ: 0 ANSI: 0 CCS
Jul 14 13:59:40 maison-desktop kernel: [   11.688221] scsi 4:0:0:1: Direct-Access     ICSI     IC1210        MS 1.6E PQ: 0 ANSI: 0 CCS
Jul 14 13:59:40 maison-desktop kernel: [   11.689479] scsi 4:0:0:2: Direct-Access     ICSI     IC1210    MMC/SD 1.6E PQ: 0 ANSI: 0 CCS
Jul 14 13:59:40 maison-desktop kernel: [   11.690735] scsi 4:0:0:3: Direct-Access     ICSI     IC1210        SM 1.6E PQ: 0 ANSI: 0 CCS
Jul 14 13:59:40 maison-desktop kernel: [   11.760334] usb 1-4.1: reset full speed USB device using ehci_hcd and address 5
Jul 14 13:59:40 maison-desktop kernel: [   11.855803] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jul 14 13:59:40 maison-desktop kernel: [   11.855854] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jul 14 13:59:40 maison-desktop kernel: [   11.857859] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jul 14 13:59:40 maison-desktop kernel: [   11.857908] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jul 14 13:59:40 maison-desktop kernel: [   11.861817] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Jul 14 13:59:40 maison-desktop kernel: [   11.861871] sd 4:0:0:2: Attached scsi generic sg4 type 0
Jul 14 13:59:40 maison-desktop kernel: [   11.936958] usb 1-4.1: reset full speed USB device using ehci_hcd and address 5
Jul 14 13:59:40 maison-desktop kernel: [   12.043673] sd 4:0:0:3: [sde] Attached SCSI removable disk
Jul 14 13:59:40 maison-desktop kernel: [   12.043729] sd 4:0:0:3: Attached scsi generic sg5 type 0
Jul 14 13:59:40 maison-desktop kernel: [   13.116236] usb 1-4.1: reset full speed USB device using ehci_hcd and address 5
Jul 14 13:59:40 maison-desktop kernel: [   15.296276] usb 1-4.1: reset full speed USB device using ehci_hcd and address 5
Jul 14 13:59:40 maison-desktop kernel: [   16.109386] type=1505 audit(1247572779.364:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2314
Jul 14 13:59:40 maison-desktop kernel: [   16.150244] type=1505 audit(1247572779.403:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2318
Jul 14 13:59:40 maison-desktop kernel: [   16.150317] type=1505 audit(1247572779.403:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2318
Jul 14 13:59:40 maison-desktop kernel: [   16.150348] type=1505 audit(1247572779.403:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2318
Jul 14 13:59:40 maison-desktop kernel: [   16.150376] type=1505 audit(1247572779.403:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2318
Jul 14 13:59:40 maison-desktop kernel: [   16.253373] type=1505 audit(1247572779.507:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2322
Jul 14 13:59:40 maison-desktop kernel: [   16.253500] type=1505 audit(1247572779.507:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2322
Jul 14 13:59:40 maison-desktop kernel: [   16.282983] type=1505 audit(1247572779.535:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2326
Jul 14 13:59:40 maison-desktop kernel: [   17.540327] usb 1-4.1: reset full speed USB device using ehci_hcd and address 5
Jul 14 13:59:40 maison-desktop kernel: [   17.721833] usb 1-4.1: reset full speed USB device using ehci_hcd and address 5
Jul 14 13:59:41 maison-desktop kernel: [   17.813579] usb 1-4.1: device firmware changed
Jul 14 13:59:41 maison-desktop kernel: [   17.814327] usb 1-4.1: USB disconnect, address 5
Jul 14 13:59:41 maison-desktop kernel: [   17.888838] usb 1-4.1: new full speed USB device using ehci_hcd and address 6
Jul 14 13:59:41 maison-desktop kernel: [   17.981957] usb 1-4.1: not running at top speed; connect to a high speed hub
Jul 14 13:59:41 maison-desktop kernel: [   17.984408] usb 1-4.1: configuration #1 chosen from 1 choice
Jul 14 13:59:41 maison-desktop kernel: [   17.985169] scsi5 : SCSI emulation for USB Mass Storage devices

I see that "not running at top speed; connect to a high speed hub"

I read some thread where they are talking about ehci or ohci, but they are not present on my kernel modules.
It's not interessant to have a computer on USB1, t's very slow , max 1Mbits.

Thanx in advance.

---

### Post by macal94 on 2009-07-16
Any idea to begin the debug ??

I'm adding some more commands : 

maison@maison-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
01:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
maison@maison-desktop:~$ uname -a
Linux maison-desktop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

---

### Post by khelben1979 on 2009-07-16
Have you checked your BIOS settings?

Have you considered getting a pci card with usb ports?

---

### Post by macal94 on 2009-07-16
Yes khelben1979, I've already check the BIOS config.

And this midday, I've bought an additional PCI card with USB2.
I hope it will run correctly this evening.

What do you think , it's a kernel issue to support the ICH7 chipset ?

Thanks.

---

### Post by khelben1979 on 2009-07-16
I think it's mostly likely that it is a kernel issue, however, there could be working support with the kernel version which could enable usb2 support for your system. You need another kernel with this support or compile one yourself (not easy).

I have an Belkin USB card myself which works excellent with Linux. That would be the one I would recommend if you hadn't already chosen one.

---

### Post by macal94 on 2009-07-16
Hi khelben1979, it's clear now that it's an issue with the support of ICH7 by the kernel.

I've bought an USB additional card with a chipset NEC (from connectland) and all devices are on USB2 now.

How I can request an kernel support to resolve this issue ?

To finalise the investigation, I'm dwonloading now the ubuntu 8.04.02 to try if an old kernel have a better support.

Thanks

For information.
maison@maison-desktop:~$ lsusb 
Bus 002 Device 006: ID 0dda:2026 Integrated Circuit Solution, Inc. USB2.0 Card Reader
Bus 002 Device 004: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 002 Device 002: ID 04a9:221b Canon, Inc. CanoScan 4200F
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 03f0:8704 Hewlett-Packard deskjet 5900 series
Bus 003 Device 002: ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c513 Logitech, Inc. MX3000 Cordless Desktop Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
maison@maison-desktop:~$ lspc
lspci     lspcmcia  
maison@maison-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
01:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
03:00.0 USB Controller: NEC Corporation USB (rev 43)
03:00.1 USB Controller: NEC Corporation USB (rev 43)
03:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
maison@maison-desktop:~$ uname -a
Linux maison-desktop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

---

### Post by diiphantom on 2009-09-15
> **macal94 said:**
> ...

Macal94, i just put together a pc with this motherboard, running ubuntu 9.04, but my sound doesnt work, did you have this issue?


Asus P5QPL-VM EPU
core 2 Duo
PNY 9500 gt 1gig mem

can you help me? thanks!

---

### Post by khelben1979 on 2009-09-15
I think the best way is to learn how to compile your own Linux kernel if you want full USB 2.0 support on all these ports. Are you sure they really are 2.0?

[Check this guide for more information]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html").

---

### Post by macal94 on 2009-09-15
@ diiphantom

Have you configure on your Bios the sound on AC97, i don't knwo if HD sound works correctly on Linux.
On my side, no sound issue.

For usb2, since I've run my system on 8.04 with Live cd, now the usb2 issue desappear.
I don't know why.
I've seen on Ubuntu 9.10 that the support of Intel chipset will change, so maybe a better support.

Bye.

---

### Post by bero74 on 2009-09-16
I have this problem with the latest kernel 2.6.28-15. Reverting to kernel 2.6.28-14 solved the problem.

---


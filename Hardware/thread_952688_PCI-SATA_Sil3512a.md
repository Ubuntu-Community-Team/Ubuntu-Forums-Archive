---
title: "PCI-SATA Sil3512a"
date: 2008-10-19
forum: Hardware
---

### Post by CrazyByte on 2008-10-19
I don't have SATA controller on motherboard on my home server, so I've bought some pci card with Sil3512a chipset. I've installed it on computer and nothing happened. I still can't see it in gparted application. On CD there is some *.c and *.h files and doc-file with instruction for Red Hat. Is there some native ways to make it work with Ubuntu, or I need to recompile kernel with this driver somehow?
P.S. Ubuntu 8.10 beta
P.P.S.:
lspci:
00:00.0 Host bridge: VIA Technologies, Inc. P4X333/P4X400/PT800 AGP Bridge (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:08.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY (rev 31)
00:09.0 Unclassified device [0004]: Silicon Image, Inc. Device 3412 (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)

---


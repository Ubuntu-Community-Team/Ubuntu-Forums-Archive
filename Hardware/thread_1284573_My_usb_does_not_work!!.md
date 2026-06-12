---
title: "My usb does not work!!"
date: 2009-10-06
forum: Hardware
---

### Post by chris_lukehart on 2009-10-06
My computer doesn't display usb devices. The command lsusb displays nothing. The command lshw says my usb is unclaimed. 

command lshw:  
         
                                    *-usb:0 UNCLAIMED
                                                    description: USB Controller
                                                    product: IXP SB400 USB Host Controller
                                                    vendor: ATI Technologies Inc
                                                    physical id: 13
                                                    bus info: pci@0000:00:13.0
                                                    version: 00
                                                    width: 32 bits
                                                    clock: 66MHz
                                                    capabilities: msi cap_list
                                                    configuration: latency=64
                                           

*-usb:1 UNCLAIMED
                                       description: USB Controller
                                       product: IXP SB400 USB Host Controller
                                       vendor: ATI Technologies Inc
                                                    physical id: 13.1
                                                    bus info: pci@0000:00:13.1
                                                    version: 00
                                                    width: 32 bits
                                                    clock: 66MHz
                                                    capabilities: msi cap_list
                                                    configuration: latency=64
                                           

*-usb:2 UNCLAIMED
                                                   description: USB Controller
                                      product: IXP SB400 USB2 Host Controller
                                      vendor: ATI Technologies Inc
                                                   physical id: 13.2
                                                   bus info: pci@0000:00:13.2
                                                   version: 00
                                      width: 32 bits
                                                   clock: 66MHz
                                                   capabilities: pm msi cap_list
                                                   configuration: latency=64

---

### Post by chris_lukehart on 2009-10-06
I am using Ubuntu 9.04 Desktop Edition. 

bump

---

### Post by chris_lukehart on 2009-10-06
Lsusb command still displays nothing.

bump!

---

### Post by dummy910 on 2009-10-06
The answer is right here on this board:
[http://ubuntuforums.org/showpost.php?p=4453632&postcount=2](http://ubuntuforums.org/showpost.php?p=4453632&postcount=2)
> Please turn off your computer. Unplug ALL usb devices, memory, usb harddrives, printer, scanner, ALL. Restart Ubuntu in Recovery mode. When it has finished loading, logout with:

shutdown -r now

restart normally. Shutdown, again, without restart. Plug in one (1) usb device. Restart. See if lsusb lists it. If yes, you are good to go. [color=red]If no, post the output of lspci and lsusb here[/color].

---

### Post by chris_lukehart on 2009-10-06
[COLOR=red]output of lspci:[/COLOR]

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:00.0 VGA compatible controller: nVidia Corporation D9M-20 [GeForce 9400 GT] (rev a1)
03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
03:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

---

### Post by chris_lukehart on 2009-10-06
bump!!

---

### Post by chris_lukehart on 2009-10-06
bump!!!

---


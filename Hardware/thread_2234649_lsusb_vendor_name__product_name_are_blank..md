---
title: "lsusb vendor name / product name are blank."
date: 2014-07-15
forum: Hardware
---

### Post by WinEunuchs2Unix on 2014-07-15
My USB list includes two entries 2109:0812 and 2109:2812 that have blank names.

```
[FONT=Ubuntu Medium]~$lsusb[/FONT][FONT=Courier 10 Pitch]Bus002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/FONT]
[FONT=Courier 10 Pitch]Bus007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/FONT]
[FONT=Courier 10 Pitch]Bus006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/FONT]
[FONT=Courier 10 Pitch]Bus005 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0for Bluetooth [/FONT]
[FONT=Courier 10 Pitch]Bus005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/FONT]
[FONT=Courier 10 Pitch]Bus009 Device 007: ID 174c:5136 ASMedia Technology Inc. [/FONT]
[FONT=Courier 10 Pitch]Bus009 Device 006: ID 0951:1666 Kingston Technology [/FONT]
[FONT=Courier 10 Pitch]Bus009 Device 005: ID **2109:0812**  [/FONT]
[FONT=Courier 10 Pitch]Bus009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub [/FONT]
[FONT=Courier 10 Pitch]Bus008 Device 005: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter [/FONT]
[FONT=Courier 10 Pitch]Bus008 Device 004: ID 1004:618e LG Electronics, Inc. Ally/OptimusOne/Vortex (debug mode) [/FONT]
[FONT=Courier 10 Pitch]Bus008 Device 003: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB [/FONT]
[FONT=Courier 10 Pitch]Bus008 Device 002: ID **2109:2812**  [/FONT]
[FONT=Courier 10 Pitch]Bus008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/FONT]
[FONT=Courier 10 Pitch]Bus001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0multicard reader [/FONT]
[FONT=Courier 10 Pitch]Bus001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd [/FONT]
[FONT=Courier 10 Pitch]Bus001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/FONT]
[FONT=Courier 10 Pitch]Bus004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/FONT]
Bus003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```

2109:0812 should read "VIA Labs Inc. USB 3.0 - 4 port hub".
2109:2812 should read "VIA Labs Inc. USB 2.0 (Backside) - 4 port hub".

Device 2109 is a 4 port powered hub supporting Superspeed USB 3.0 5000 Mbps along with High-speed USB 2.0 480 Mbps.

I tried editing /etc/udev/rules.d/70-persistent-net.rules (the only file there) with the commands:
```
SUBSYSTEMS=="usb", IMPORT{program}="usb-db %p"
SUBSYSTEMS=="pci", IMPORT{program}="pci-db %p"
```

This was recommended on a website but frowned upon by Greg K-H.  It didn't work.

Then I tried ATTR / ATTRS (very confusing):
```
ATTR{idVendor}=="2901", ATTR{idProduct}=="0812", ATTR{manufacturer}="VIA Labs Inc.   ", ATTR{product}="USB 3.0 4 Port Hub"
ATTR{idVendor}=="2901", ATTR{idProduct}=="2812", ATTR{manufacturer}="VIA Labs Inc.   ", ATTR{product}="USB 2.0 Backside 4 Port Hub"
```

I suspect I need more matches like SUBSYSTEM=="USB" or ACTION=="Add" or something like that???

I also checked the [CENTER][COLOR=#0000FF][FONT=Times New Roman]The USB ID Repository - [/FONT][/COLOR][COLOR=#0000FF][FONT=Times New Roman]The home of the [/FONT][/COLOR][/CENTER]usb.ids[CENTER][COLOR=#0000FF][FONT=Times New Roman] file [/FONT][/COLOR][/CENTER]USB device database on the net and although it doesn't specifically have the vendor name formatted exactly right it does have it in the comment section, re: [https://usb-ids.gowdy.us/read/UD/2109/2812](https://usb-ids.gowdy.us/read/UD/2109/2812)

I ran [FONT=Ubuntu Medium]$sudo udevadm monitor --udev –property > udevadm_monitor.txt

[/FONT]```
UDEV [3696.352895] add     /devices/pci0000:00/0000:00:1c.4/0000:08:00.0/usb9/9-1 (usb)[FONT=Courier 10 Pitch]ACTION=add[/FONT]
[FONT=Courier 10 Pitch]BUSNUM=009[/FONT]
[FONT=Courier 10 Pitch]DEVNAME=/dev/bus/usb/009/002[/FONT]
[FONT=Courier 10 Pitch]DEVNUM=002[/FONT]
[FONT=Courier 10 Pitch]DEVPATH=/devices/pci0000:00/0000:00:1c.4/0000:08:00.0/usb9/9-1[/FONT]
[FONT=Courier 10 Pitch]DEVTYPE=usb_device[/FONT]
[FONT=Courier 10 Pitch]ID_BUS=usb[/FONT]
[FONT=Courier 10 Pitch]ID_FOR_SEAT=usb-pci-0000_08_00_0-usb-0_1[/FONT]
[FONT=Courier 10 Pitch]ID_MODEL=USB3.0_Hub[/FONT]
[FONT=Courier 10 Pitch]ID_MODEL_ENC=USB3.0\x20Hub\x20\x20\x20\x20\x20\x20\x20[/FONT]
[FONT=Courier 10 Pitch]ID_MODEL_FROM_DATABASE=3.0root hub[/FONT]
[FONT=Courier 10 Pitch]ID_MODEL_ID=0812[/FONT]
[FONT=Courier 10 Pitch]ID_PATH=pci-0000:08:00.0-usb-0:1[/FONT]
[FONT=Courier 10 Pitch]ID_PATH_TAG=pci-0000_08_00_0-usb-0_1[/FONT]
[FONT=Courier 10 Pitch]ID_REVISION=0701[/FONT]
[FONT=Courier 10 Pitch]**ID_SERIAL=VIA_Labs__Inc._USB3.0_Hub**[/FONT]
[FONT=Courier 10 Pitch]ID_USB_INTERFACES=:090000:[/FONT]
[FONT=Courier 10 Pitch]ID_VENDOR=VIA_Labs__Inc.[/FONT]
[FONT=Courier 10 Pitch]ID_VENDOR_ENC=VIA\x20Labs\x2c\x20Inc.\x20\x20\x20[/FONT]
[FONT=Courier 10 Pitch]**ID_VENDOR_FROM_DATABASE=LinuxFoundation**[/FONT]
[FONT=Courier 10 Pitch]ID_VENDOR_ID=2109[/FONT]
[FONT=Courier 10 Pitch]MAJOR=189[/FONT]
[FONT=Courier 10 Pitch]MINOR=1025[/FONT]
PRODUCT=2109/812/701
```

Above is a subset of the full output.  Linux Foundation does have hubs too but that uses a different Vendor ID and Product ID.

dmesg output has nothing extraordinary. Likewise /var/log/syslog and /var/log/kern.log have nothing out of the ordinary.

Using Ubuntu 14.04 LTS and tried with Kernel Version 3.13.0.24, 3.13.0.29, 3.15.1, 3.15.2, 3.15.3, 3.15.4 and 3.15.5.  

Windows Vista-32 doesn't report any errors on the hub however it is attached 2.5 Gbps ASM 1042 (aka ASM 2105) PCIe 1.0 54mm ExpressCard with two USB 3.0 ports where windows does report an "unknown" device error which doesn't seem to impact anything.  That said I don't use Windows very much these days.
 
Any solutions would be greatly appreciated but more places to search would be good too.  After 3 weeks off and on I'm running out of google searches :(

---

### Post by WinEunuchs2Unix on 2014-08-04
Problem was [solved] today.  Output proof:

```
/var/lib/usbutils$ sudo gedit usb.ids

/var/lib/usbutils$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 013: ID 174c:5136 ASMedia Technology Inc. 
Bus 009 Device 012: ID 0951:1666 Kingston Technology 
Bus 009 Device 011: ID 2109:0812 VIA Labs Inc. USB 3.0 4 port hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 005: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 008 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 008 Device 002: ID 2109:2812 VIA Labs Inc. USB 3.0 4 port hub USB 2.0 backside
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

The usb.ids file used by the lsusb command didn't have up to date vendor / product naming information.  It was dated from May 17th, 2014 the date of Ubuntu install and never updated by "sudo apt-get update" commands.  Whilst editing the file the following vendor / product names (in bold) were added:

```

2101  ActionStar
	0201  SIIG 4-to-2 Printer Switch
**2109  VIA Labs Inc.**
**	0812  USB 3.0 4 port hub**
**	2812  USB 3.0 4 port hub USB 2.0 backside**
2162  Creative (?)
	2031  Network Blaster Wireless Adapter
	500c  DE5771 Modem Blaster
	8001  Broadxent BritePort DSL Bridge 8010U
```

Solution was possible by lots of googling and stumbling upon unrelated problems that yielded clues.

---

### Post by Yellow Pasque on 2014-08-04
```
sudo update-usbids
```
;)

(See also: update-pciids)

---

### Post by WinEunuchs2Unix on 2014-08-04
> **Temüjin said:**
> ```
sudo update-usbids
```
;)

(See also: update-pciids)

typing "sudo update-usbids" was a wonderful way of wiping out my new manufacturer name "VIA Labs Inc." for vendor id: 2109... LOL

Luckily I made a copy first :P

EDIT: The important point isn't how to get usb.ids updated but rather when lsusb shows blank names for manufacturers this file needs to be changed.

---


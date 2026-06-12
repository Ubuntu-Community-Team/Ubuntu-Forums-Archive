---
title: "[SOLVED] Wireless card on lenovo y410 (broadcom 4310) not detected"
date: 2008-08-27
forum: Hardware
---

### Post by abhishekrane on 2008-08-27
Well i have checked all the posts for broadcomm and couldnt get t working yet.I have tried already by bcm43xx b43-fwcutter and ndiswrapper but wireless card is not detected.It works great in xp though.i have messed up a bit by installing by both methods still no use.any help?
D
no driver is showing up in System>Administration>Restricted Drivers

```

abhishek@lenovo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
abhishek@lenovo:~$ 

```

```

abhishek@lenovo:~$ ndiswrapper -l
bcmwl5 : driver installed

```

```
abhishek@lenovo:~$ b43-fwcutter -l
b43-fwcutter version 011

Extracting firmware is possible from these binary driver files.
The <ID> column shows the unique identifier string for your firmware.
You must select the firmware with the same ID as printed by the kernel driver on modprobe.
Note that only recent drivers print such a message on modprobe.
Please read http://linuxwireless.org/en/users/Drivers/b43#devicefirmware

<driver>	<filename>		<microcode>	<ID>	<MD5 checksum>

b43legacy	wl_apsta.o		295.14		FW10	e08665c5c5b66beb9c3b2dd54aa80cb3
b43		wl_apsta.o		351.126		FW11	9207bc565c2fc9fa1591f6c7911d3fc0
b43		wl_apsta_mimo.o		351.126		FW11	722e2e0d8cc04b8f118bb5afe6829ff9
b43		wl_apsta_mimo.o		410.2160	FW13	cb8d70972b885b1f8883b943c0261a3c

abhishek@lenovo:~$ 

```

---

### Post by abhishekrane on 2008-08-29
solved using this post
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---


---
title: "Dell XPS m1730 + wireless internet"
date: 2008-08-14
forum: Hardware
---

### Post by mike770780 on 2008-08-14
Hello

I have a Dell XPS m1730 with a built in wireless card that is not working as expected. 

The card itself cannot be seen inside the Ubuntu network manager and is not  detected by lspci . I know it's nothing physical because in Windows the card works as expected. For those who know Dell XPS laptops the LED on the chassis that indicates a working wifi card is off. 

Dell tech support refuses to provide help for Linux, so I'm pretty much stuck. 

I've attached lspci outout, any help is appreciated.

Thanks
Mike


root@ubuntu:/home/mike# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:01.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8700M GT (rev a1)
04:00.0 3D controller: nVidia Corporation GeForce 8700M GT (rev a1)
05:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
05:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
0f:00.0 Class ff00: AGEIA Technologies, Inc. Unknown device 0000

---

### Post by bpl07 on 2008-08-14
Nevermind, see below

---

### Post by StormPCs on 2008-08-14
No, thats the wired NIC.

This is the wireless: Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


Get an Intel based wireless and your problem will be solved.

---

### Post by bpl07 on 2008-08-14
> **StormPCs said:**
> No, thats the wired internet.

This is the wireless: Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


Ahh, you're right.  In that case, normally you would use [b43-fwcutter]("http://linuxwireless.org/en/users/Drivers/b43#unsupported"), but they haven't reverse-engineered the code yet.

If you're willing to try ndiswrapper here is a site that describes how to [install the windows driver in linux]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper").

---

### Post by macabro22 on 2008-11-04
> **StormPCs said:**
> No, thats the wired NIC.

This is the wireless: Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


Get an Intel based wireless and your problem will be solved.

Weird, here's what came packed into my beast:
```

0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61
```)

It works out of the box

---

### Post by dront78 on 2008-11-09
it should work natively with proprietary broadcom driver
read
[http://djkaos.wordpress.com/2008/10/25/installing-broadcom-80211-linux-sta-driver/](http://djkaos.wordpress.com/2008/10/25/installing-broadcom-80211-linux-sta-driver/)
and
[http://djkaos.wordpress.com/2008/10/31/fixing-broadcom-80211-linux-sta-driver/](http://djkaos.wordpress.com/2008/10/31/fixing-broadcom-80211-linux-sta-driver/)

---


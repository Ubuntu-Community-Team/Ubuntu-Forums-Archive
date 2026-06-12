---
title: "Wireless Not working"
date: 2010-01-24
forum: Hardware
---

### Post by BenSchrock on 2010-01-24
OK so I am really new to Linux but I have heard a lot about it so I would like to try it out and learn. I created a usb live disk of ubuntu. It also has persistence. I currently have a dell 1505 mini wifi card and I do not know how to install the driver into linux. Can anyone help? We will really have to start at the beginning.

---

### Post by Greenwidth on 2010-01-24
Best way to start is to identify the chipset on the card, open a terminal and type 
```
lspci
``` 
and post the results here.

---

### Post by BenSchrock on 2010-01-24
```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 7930 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS7932 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Device 7934
00:06.0 PCI bridge: ATI Technologies Inc RS7936 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Device 7937
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Xpress 1250
03:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:01.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
ubuntu@ubuntu:~$ 
```

---

### Post by BenSchrock on 2010-01-24
Also my touchpad isnt working. I am having to use a usb mouse. But we can talk about that later maybe.

---

### Post by Greenwidth on 2010-01-24
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
is the wireless card, which some, it seems, have had trouble with.

Easiest way to install the STA driver is connect wired, do your updates (System > Admin > Update Manager) then look in System Admin > Hardware Drivers for it, activate and restart.

If you have troubles with it afterwards it may be you need to see this:
[http://www.ubuntugeek.com/fix-for-broadcom-4328-v3-wireless-problem-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/fix-for-broadcom-4328-v3-wireless-problem-in-ubuntu-9-10-karmic.html)

---


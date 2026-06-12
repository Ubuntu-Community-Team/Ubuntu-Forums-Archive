---
title: "Verizon Samsung n150 Broadband Access?"
date: 2010-08-03
forum: Hardware
---

### Post by newtolinuxbutloveit on 2010-08-03
Hello everyone.  I recently purchased a Verizon Samsung n150 netbook.   It was so slow with the Win7 starter on it I had to ditch it in favor of the Ubuntu 9.10 Netbook Remix.   It picked up everything right out of the bat, even on the live iso.   Ethernet, Wifi, Cam, Sound, etc etc.   So I went ahead and installed it.  It is atleast 5x faster then before with the Win7.   

My only complaint is that I cannot figure out how to/where to access the mobile broadband card.  It is the built in one with the Verizon sim inserted into the slot under the battery.  I cannot find any information about the brand or model number or anything of the device so I don't know if it detected or not.

I did an lspci and here is the output;

00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

Even when I check the driver downloads for this system from Verizon I only see drivers for ;

Wireless LAN,ATHEROS
Lan
Bluetooth,BROADCOM
VGA(Graphics),INTEL
Chipset
Sound(Audio)
IMSM
Touchpad
Wireless LAN,REALTEK

I'm not even sure which one of those it should be?  If I knew maybe I could try the use ndiswrapper.  

I can go to Network Connections and can add a Mobile Broadband connection with my phonenumber and password and everything, but how do I connect to it?  I cannot find it anywhere.  

I have spent hours and hours searching everywhere for this issue. I see lots of reference to PC Cards and USB WWAN devices but no on board ones.  

Please can someone help me figure this out.  Its so slow that I want to take it back if I have to use Win7 but I thought for sure I would be able to get this to work so I deleted the recovery partition which I hear violates the warranty so I'm stuck with this thing.  

Thanks for reading this.

---

### Post by JRSeys on 2010-08-21
I've got the same problem.  It turns out the modem is not a PCI device: it's on USB (internally).

lsusb doesn't provide much useful information either, just that there is a Qualcomm device.  Windows, however, will let you know that the modem is in fact a Gobi 2000 HS USB Mobile Broadband device.

That led me to this bug report, which I am still trying to figure out.  It looks like some people have had success with the kernel drivers discussed here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/+index?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099/+index?comments=all")

        --Justin

---


---
title: "Inspiron M5030 Troubles"
date: 2012-08-23
forum: Hardware
---

### Post by TomSwift98 on 2012-08-23
Hey guys! I recently installed linux alongside win7 on a Dell Inspiron M5030.

My first problem stems from Unity. I can run Unity2D fine, but when I switch to 3D the desktop loads, with all my icons, but the interface never loads and the mouse/keyboard commands do nothing.
I attempted to fix this by adding nomodese to grub, but it had no effect.

My second problem is video rendering/acceleration.  On my win7 partition, vlc can play a video in full screen with no issues, but on ubuntu (and Unity2D) it has lag, shrinking the size of the vlc window eliminates this, but I want my fullscreen back! My gpu is a ATI Radeon HD 4250 and I appear to have the drivers installed, but I am not sure how to test this.  Could this be related to my Unity issue?

My final issue is my Logitech M305 wireless mouse.  It moves around the screen but is very laggy.  Any ideas?

---

### Post by jolubaes on 2012-10-07
I have a dell inspirion m501R with the same gpu and the same problem... just 2D it's working. I have tried all the possible drivers and nothing has work so far. I would be very interesting if someone has any suggestion

---

### Post by typhoon_tip on 2012-10-07
First thing you can do, is post the output of:
```
lspci
```

---

### Post by jolubaes on 2012-10-29
sorry for the late response...

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Dell Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by typhoon_tip on 2012-11-01
You have a Radeon HD 4200 series, it is compatible with the Legacy Driver from ATI (you need to install the driver manually, you can follow the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29))

Just remember, DO NOT download the file indicated in the Wiki, instead download this one !!
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

This is the Legacy Driver, it can be installed in 12.04 (not sure about 12.10).

Installation instructions and pre-requisites are the same, just change the filename when necessary in the commands explained in the Wiki.

---


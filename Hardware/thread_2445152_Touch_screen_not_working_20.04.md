---
title: "Touch screen not working 20.04"
date: 2020-06-09
forum: Hardware
---

### Post by mfcarpino on 2020-06-09
I did a fresh install on my HP X-360 with Ubuntu 20.04 and noticed that the touch screen isn't working.  If I boot my system with Windows to Go - W10 on a external hard drive the touch screen works.  I'd like to get the touch screen to work.  Does anyone have any thoughts on how I can fix this issue?

---

### Post by CelticWarrior on 2020-06-10
Welcome.

Please identify the actual device. Run 'lspci' and/or 'lsusb' to find out.

---

### Post by mfcarpino on 2020-06-18
```
lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h (Models 30h-3fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 05)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h (Models 30h-3fh) Host Bridge
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.5 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Kabini/Mullins PSP-Platform Security Processor
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h (Models 30h-3fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h (Models 30h-3fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h (Models 30h-3fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h (Models 30h-3fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h (Models 30h-3fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h (Models 30h-3fh) Processor Function 5
01:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 07)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
```

---

### Post by mfcarpino on 2020-06-18
```
lsusb
Bus 002 Device 004: ID 064e:c342 Suyin Corp. 
Bus 002 Device 003: ID 06cb:014f Synaptics, Inc. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. Root Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0cf3:3121 Qualcomm Atheros Communications 
Bus 001 Device 004: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. Root Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by mfcarpino on 2020-06-18
Thanks for your help.  The other thing I've discovered is the touchscreen works with 20.04 for a few seconds when the desktop loads and then it stops.

---

### Post by slickymaster on 2020-06-18
*Thread moved to **Hardware**.*

---

### Post by mfcarpino on 2020-07-09
This issue at least how I was able to get the touch screen to work was because the Snap Store wasn't properly installing with a new install of 20.04.  How I resolved the issue and to get the touch screen to work was to remove and then install Snap Store.

I just ran these 2 commands in the terminal and my touch screen works.

sudo snap remove snap-store

sudo snap install snap-store


*** If the computer goes into power saving mode (ie suspend) the touch screen sometimes stops working.  I'm OK for now with restarting the OS if I need to use the touch screen after a power saving restart until someone implements a fix.

---


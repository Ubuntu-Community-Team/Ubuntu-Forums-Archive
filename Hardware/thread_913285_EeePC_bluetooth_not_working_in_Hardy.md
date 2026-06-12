---
title: "EeePC bluetooth not working in Hardy"
date: 2008-09-07
forum: Hardware
---

### Post by khm on 2008-09-07
Hi,

I have an Eee 900 with Hardy installed (kernel 2.6.24-21-eeepc).  For kernel info see [www.array.org/ubuntu](www.array.org/ubuntu)

The only thing I have been unable to get workign is the bluetooth.  I have a Logitech v470 which I can see from my cell phone (thus indicating that signal is not a problem).  I have gone to System->Preferences->Bluetooth and verified that 'Input Service' is running. I go to add device and nothing shows up.  It doesn't look like the internal bluetooth card is even recognized. My results from a lspci:

kmonday@kmonday-eeepc:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)


I don't see anything related to bluetooth.....

Any ideas?

---

### Post by jcostom on 2008-09-07
> **khm said:**
> Hi,

I have an Eee 900 with Hardy installed (kernel 2.6.24-21-eeepc).  For kernel info see [www.array.org/ubuntu](www.array.org/ubuntu)

.......

I don't see anything related to bluetooth.....

Any ideas?

The BT radio is not a PCI device, but rather a USB one.  Check your BIOS settings to be sure the device is active by default, and then use your configured hotkeys to make sure it's activated.  If BT is on, you'll have the little BT icon in the notification area, near the clock.

It works out of the box on my eee 1000, using the same kernel you mentioned..

---

### Post by khm on 2008-09-07
> **jcostom said:**
> The BT radio is not a PCI device, but rather a USB one.  Check your BIOS settings to be sure the device is active by default, and then use your configured hotkeys to make sure it's activated.  If BT is on, you'll have the little BT icon in the notification area, near the clock.

It works out of the box on my eee 1000, using the same kernel you mentioned..

Okay, it makes sense that the bluetooth is not a PCI device. There is control for PCI devices via the BIOS, but as far as I can tell there is no control for USB devices. In the bluetooth preferences, there are options for the Notification Area:

[I]Never display icon
Only display icon when adapter present
Always display icon[/I]

It is currently set to O*nly display when adapter present*. Does this mean that the OS is not recognizing the device at all, or does this mean that the device is not active?

I have no experience dealing with bluetooth, so any help is appreciated.

Thanks!

PS  - just noticed that with the icon set to *Always display* and after left clicking the icon, there are two options that area greyed out: *Send file...*, and *Browse Device...*

---

### Post by khm on 2008-09-07
oh... and here's my *lusb* results:

kmonday@kmonday-eeepc:~$ lsusb
Bus 004 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0951:1606 Kingston Technology 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

I think the Chicony device is the webcam nd the Kingston is a thumbdrive (not connected... ?)

---


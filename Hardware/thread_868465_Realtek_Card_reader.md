---
title: "Realtek Card reader"
date: 2008-07-23
forum: Hardware
---

### Post by Bigdaddychops on 2008-07-23
hello there, i am having a problem with my gateway m-1626 and its built-in Realtek USB 2.0 card reader. I have ignored this problem long enough, and i would like to get some definitive answers. When i insert a Mem. Card, there is some hard drive activity, but to no avail. any help would be appreciated.

---

### Post by Dark_Stang on 2008-07-23
What's the output of "lsusb"?

---

### Post by Bigdaddychops on 2008-07-23
Bus 006 Device 005: ID 045e:0710 Microsoft Corp. 
Bus 006 Device 003: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Dark_Stang on 2008-07-23
O.o

Okay, so the card reader doesn't appear to be hooked up USB. What's the output of lspci?

---

### Post by Bigdaddychops on 2008-07-23
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

---

### Post by Dark_Stang on 2008-07-23
Uhm... I don't see anything that might be a card reader. For example, this is the card reader section of lspci from my laptop...
```
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

Did/does it work in windows?

---

### Post by Bigdaddychops on 2008-07-23
that's what makes me think it's a hardware problem, i never tried it in windows, but it would be hard to do seeing as how i didn't even agree to the EULA, so i will never know.

What about the lsusb that talks about the realtek semiconductor, is that the wireless? i think that it is.

---

### Post by Dark_Stang on 2008-07-23
The "ID 0bda:8189 Realtek Semiconductor Corp." is your wireless card. I think you've got hardware issues.

---

### Post by Bigdaddychops on 2008-07-23
just as suspected, and lamented. All-well, thanks though.
Kudos.:)

---

### Post by Dark_Stang on 2008-07-24
Wait, gateways come with the OS disk. If you wanted to you could backup your stuff, use the windows disk to try to re-install vista to confirm it's hardware. It's going to be annoying because you don't have a drivers disk though, but this way you'd know for sure.

Unless you're still in the return policy, then exchange that thing. If it's outside the exchange period but under warranty, take it to the store you bought it from and have them ship it off to be fixed.

---

### Post by Leo Damascus on 2009-02-02
You have the exact same computer I do.  Here's how I fixed those problems:

Run the following.
```
gksu gedit /etc/rc.local
```
When gedit opens up the rc.local file, make sure it looks like this:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe mac80211
modprobe rtl8187
ifconfig wlan0 up
iwconfig wlan0 rate 11M fixed
ifconfig wlan0 mtu 1420

exit 0

```
Then reboot.  This will fix several issues with the rtl8187b wireless card.  It may not be a perfect solution, but it'll help a lot.

---

### Post by sargeant dread on 2009-03-18
Thank you, Leo Damascus, this seemed to have helped with my internet problem

---

### Post by fstrube on 2010-05-20
I had the same issue on my Dell Vostro 3500 laptop, running Ubuntu 10.04.  The solution (as per [http://hardware4linux.info/component/33167/](http://hardware4linux.info/component/33167/)) was solved by running 

```
# sudo modprobe usb-storage
```

If this solves your problem, try adding usb-storage to your /etc/modules file so that when your computer restarts it will automatically load the usb-storage module.

---


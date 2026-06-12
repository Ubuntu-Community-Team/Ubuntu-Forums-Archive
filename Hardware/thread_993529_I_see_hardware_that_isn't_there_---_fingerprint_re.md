---
title: "I see hardware that isn't there --- fingerprint reader"
date: 2008-11-25
forum: Hardware
---

### Post by version7x on 2008-11-25
I've just unboxed my dell latitude e6500.  I've installed Intrepid and everything so far has worked out of the box... except the fingerprint reader.

I was attempting to configure it using this tutorial:

[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Intrepid](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Intrepid)

However, when i try to acquire the fingerprint, here's my result:

$ tf-tool --acquire

ThinkFinger 0.3 ([http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/))
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.


I'm looking right at the hardware on my laptop.  I can't find anything in the bios that turns it on or off... and dont see it.  Here's the hardware I do see:

$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0c45:63f8 Microdia 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:5802 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 413c:8156 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8158 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:8157 Dell Computer Corp. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 06eb (rev a1)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
 


Any suggestions?

Thanks in advance!

-M

---

### Post by version7x on 2008-11-26
I've now also attempted fprint at this point and it's still not seeing the reader.

I don't know what else to check... there's obviously not getting the correct module to associate with the hardware -  when I tried thinkfinger, i manually loaded the uipoint module and still nothing.

Does this sound like anything anyones found an answer to?

---

### Post by eengstrom on 2009-01-11
Your fingerprint reader is here:

Bus 003 Device 002: ID 0a5c:5802 Broadcom Corp. 

Try lsusb -v 003:002 the broadcom device is connected to both the fingerprint reader and the smart card.

I have not been able to make it work yet...

---

### Post by version7x on 2009-01-19
Ah ha!

Now I've got my usb/head on straight.  

Even though you haven't made any progress getting it to work, I'm thankful for the reply... and the education!

I'll start banging on it again now.

-M

---


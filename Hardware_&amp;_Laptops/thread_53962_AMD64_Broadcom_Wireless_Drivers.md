---
title: "AMD64 Broadcom Wireless Drivers"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by kokomo on 2005-08-02
Ok, so I know my Broadcom 4318 wireless device works under a 32-bit kernel.  But I decided to install the AMD64 kernel because I found the 64-bit drivers for the Broadcom 4318 802.11b/g wireless device.  Everything loads smoothly, ndiswrapper -i  ....to.... modprobe ndiswrapper... dmesg contains no errors(see below).  lspci is also below.

Anyways, the problem that I'm having is that when I run iwconfig I get the following error message above just above wlan0:

> Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

I'm not able to set the ESSID, or scan for my AP with the iwlist tool.

Does anyone know a resolution to this problem?
Are there any more 64-bit drivers(compiled with version 18) available for Broadcom 4318?

Thanks,
Mike



**dmesg output:**

> ndiswrapper version 1.2 loaded (preempt=no,smp=no)
ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
ACPI: PCI interrupt 0000:03:02.0[A] -> GSI 21 (level, low) -> IRQ 21
ndiswrapper: using irq 21
wlan0: ndiswrapper ethernet device 00:90:4b:f6:8a:96 using driver bcmwl5, configuration file 14E4:4318.5.conf
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP

**lspci -v output (broadcom device only):**

> 0000:03:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 1355
        Flags: bus master, fast devsel, latency 64, IRQ 21
        Memory at b0204000 (32-bit, non-prefetchable) [size=8K]

The drivers I used are available here:
[http://www.runithard.com/HOWTO-BCOM64WIRELESS/](http://www.runithard.com/HOWTO-BCOM64WIRELESS/)
and here:
[http://www.ubuntuforums.org/showthread.php?t=52201](http://www.ubuntuforums.org/showthread.php?t=52201)

I've tried the generic 64-bit broadcom drivers, but only the Acer broadcom 4318 drivers detect my hardware.

---


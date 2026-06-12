---
title: "install two different sets of linux tv media drivers at the same time"
date: 2015-02-21
forum: Hardware
---

### Post by fritz7 on 2015-02-21
Hi to all. I really need your help and expertize to try to find a solution to the problem. I have got a [DVBSky S952]("http://linuxtv.org/wiki/index.php/DVBSky_S952") PCIe card and a Cinergy T Stick RC USB-stick which is 3. Revision USB-ID 0ccd:00d3

Out of the box my ubuntu server 14.04.1 LTS only recognizes the USB receiver so I installed the drivers for the PCIe card from their [website]("http://www.dvbsky.net/Support_linux.html") while doing that I realized that there is a message "Removing obsolete files from ..." which says that it is deleting all old files/drivers. This should be no problem because it should be the full linux tv driver collection. But after rebooting die usb device is not recognized(=not listed in /dev/dvb/ ) but the PCIe card is perfectly working.

So I got the latest linux tv drivers (from their git) an installed them and the USB device was working again but the PCIe one not.

When I install the fork of the drivers for the PCIe card again it is working again but the USB one not. So I tried to copy around in the sources and also the kernel driver files but I had no plan and no success.

My kernel is 3.13.0-44-generic but i also tried 3.12 and 3.16 (same result)

I also tried another driver for the USB device i found, but also no success
[https://github.com/valtri/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0](https://github.com/valtri/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0)

thx for reading maybe someone can guid me in the right direction

---


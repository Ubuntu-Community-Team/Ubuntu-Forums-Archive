---
title: "need help to get grand dvb-t pen usb 2.0 to work"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by strug on 2006-11-14
Hello,

I'm quite new to ubuntu and have some trouble getting my dvb-t usb stick to work.

I'm using ubuntu 6.06 with a 2.6.15-27-386 kernel on an asus w5f laptop.

I found on linuxtv.org that my stick is supported:
[http://www.linuxtv.org/wiki/index.php/DVB_USB#DiBcom_USB2.0_DVB-T_devices_.28based_on_the_DiB3000M-C.2FP.29](http://www.linuxtv.org/wiki/index.php/DVB_USB#DiBcom_USB2.0_DVB-T_devices_.28based_on_the_DiB3000M-C.2FP.29)

Next, i loaded the required drivers with "sudo modprobe <driverName>":
 
 - i2c-core
 - crc32
 - firmware_class
 - dvb-core.ko
 - dvb-pll.ko

 - dib3000-common.ko
 - dib3000mc.ko
 - mt2060.ko
 - dvb-usb.ko
 - dvb-usb-dibusb-common.ko
 - dvb-usb-dibusb-mc.ko


**Problem:** Not all required driver are available (not listed in modprobe -l). Where can i get them?:confused: 

The following driver are missing and did not get installed:

 - crc32 (i got crc32c and crc16)
 - firmware_class
 - mt2060.ko

Next, i downloaded dvb-usb-dibusb-6.0.0.8.fw and copied it to /lib/firmware/2.6.15-27-386

-rw-r--r-- 1 root root 7558 2006-11-14 09:31 /lib/firmware/2.6.15-27-386/dvb-usb-dibusb-6.0.0.8.fw

When i plug in the usb stick, the log (tail /var/log/messages) just say:
Nov 14 10:00:25 little-strug kernel: [17179807.976000] usb 5-1: new high speed USB device using ehci_hcd and address 5

As fare as i understand linuxtv.org the usb stick should be detected automatically and the dvb driver should get loaded, right? (if the missing drivers are installed?)

i tried a google search and wiki/forum search as well but did not find a place of e.g. mt2060.ko.

Hope someone can help me a bit, 
thanks in advance, leif

---

### Post by strug on 2006-11-15
no hint, no tip, nothing:-k 

TIA, leif

---


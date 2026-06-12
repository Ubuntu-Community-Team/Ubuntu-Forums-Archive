---
title: "STK7700D TV Tuner on Laptop"
date: 2008-11-14
forum: Hardware
---

### Post by stevenyu on 2008-11-14
Hi Guys

I got the Asus M51Sn laptop that came with a building DVB TV Tuner STK7700D, I have try to follow the dvb-tv for linux wiki, but still no success.  Anyone of you have the same TV tuner on your PC/Laptop?

---

### Post by stevenyu on 2008-11-26
The STK7700D use the dib0700 firmware, however I can't find /dev/dvb in my system, and no dmesg regarding to the dvb device at all.


 By manual loading the dib0700 firmware via modprobe, I get the following messages


 dmesg
[ 117.476200] dib0700: loaded with support for 7 different device-types
[ 117.476296] usbcore: registered new interface driver dvb_usb_dib0700


 $lsmod | grep dvb
dvb_usb_dib0700 37128 0
dib7000p 25224 1 dvb_usb_dib0700
dib7000m 23940 1 dvb_usb_dib0700
dvb_usb 24588 1 dvb_usb_dib0700
dvb_core 86016 1 dvb_usb
dib3000mc 20616 1 dvb_usb_dib0700
dib0070 15876 1 dvb_usb_dib0700
i2c_core 31892 8 dvb_usb_dib0700,dib7000p,dib7000m,dvb_usb,dib3000mc,dibx000_common,dib0070,nvidia
usbcore 149360 7 dvb_usb_dib0700,dvb_usb,uvcvideo,btusb,ehci_hcd,uhci_hcd
 But there still no /dev/dvb??? What is going on?

---


---
title: "usb driver and modules.alias"
date: 2021-04-16
forum: Hardware
---

### Post by marksmith989898 on 2021-04-16
Hi,

I'm trying to make a usb device use a different driver by editing modules.alias.

The device is a touchscreen and uses the driver 'usbhid', I would like it to use the driver 'usbtouchscreen' to see if it solves an issue I'm having with it.

The only line in modules.alias that has 'usbhid' is: -

alias usb:v*p*d*dc*dsc*dp*ic03isc*ip*in* usbhid

So I tried adding a line with the vendor and device ID's as follows: -

alias usb:v2575p7317d*dc*dsc*dp*ic03isc*ip*in* usbtouchscreen

I restarted but it didn't work, the usb device still used 'usbhid', can anybody tell me where I'm going wrong? Or is there an easier way to do this?

Thanks,
Mark

---


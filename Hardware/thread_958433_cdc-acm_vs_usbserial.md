---
title: "cdc-acm vs usbserial"
date: 2008-10-25
forum: Hardware
---

### Post by ItsDrone on 2008-10-25
Ubuntu 8.04 32Bt

I am having an issue with my device being detected with cdc-acm rather then use usbserial_generic even when I try to force it.

The very first time of booting and connecting the device will use usbserial but after disconnecting and reconnecting it it will reroute to cdc-acm.

This is a self programmed MPU (AT90USB1287 STK525).

How the heck do I eliminate cdc-acm for good or force usbserial to us 4-2:1.1 over 4-2:1.0?

uname -a:
```
Linux ubuntu 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
```



dmesg: (first one that works)
```
[  120.923297] usb 4-2: new full speed USB device using uhci_hcd and address 2
[  121.139066] usb 4-2: configuration #1 chosen from 1 choice
[  121.142013] usbserial_generic 4-2:1.0: Generic device with no bulk out, not allowed.
[  121.142022] usbserial_generic: probe of 4-2:1.0 failed with error -5
[  121.142070] usbserial_generic 4-2:1.1: generic converter detected
[  121.142170] usb 4-2: generic converter now attached to ttyUSB0
[  121.199981] cdc_acm: probe of 4-2:1.0 failed with error -16
[  121.199993] usbcore: registered new interface driver cdc_acm
[  121.199996] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
```


after reconnecting:
```
[  154.453548] usbserial_generic 4-2:1.1: device disconnected
[  155.187917] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  155.348117] usb 4-2: configuration #1 chosen from 1 choice
[  155.351187] usbserial_generic 4-2:1.0: Generic device with no bulk out, not allowed.
[  155.351193] usbserial_generic: probe of 4-2:1.0 failed with error -5
[  155.351205] cdc_acm 4-2:1.0: ttyACM0: USB ACM device
```


/etc/udev/rules.d/90-modprobe.rules: (change to detect dev)
```
SUBSYSTEM=="usb", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2018", RUN+="/sbin/modprove usbserial 4-2:1.1  Vendor=0x03eb Product=0x2018"
```

I even removed all lines that were for cdc-acm from /lib/modules/2.6.24-21-generic/modules.usbmap

---

### Post by swinman on 2013-04-19
same exact issue with at32uc3b1512.. did you ever figure out how to get this working?

---


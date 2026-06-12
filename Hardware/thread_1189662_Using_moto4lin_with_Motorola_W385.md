---
title: "Using moto4lin with Motorola W385"
date: 2009-06-17
forum: Hardware
---

### Post by yertman on 2009-06-17
Hi All,

I am trying to get access to my Motorola W385 so I can copy pictures off the phone and add rings etc. This is proving to be quite challenging on Ubuntu 9.04. 

When I first connected the phone to my system it was not recognized and did not show up in /dev.

When I first connected my phone this is the only thing that showed up in dmesg:
```
[73318.304027] usb 2-4: new full speed USB device using ohci_hcd and address 3
[73318.558594] usb 2-4: configuration #1 chosen from 1 choice
```

Through reading some old forum posts I learned that people were having some luck using modprobe to pass the product and vendor numbers to the usbserial module. Since usbserial is now in the kernel I am now passing these arguments to the kernel. This is what is being passed to the kernel:
```
usbserial.vendor=0x22b8 usbserial.product=0x2b44
``` After doing this dmesg now shows this:

```
[73318.304027] usb 2-4: new full speed USB device using ohci_hcd and address 3
[73318.558594] usb 2-4: configuration #1 chosen from 1 choice
[73318.560561] usbserial_generic 2-4:1.0: generic converter detected
[73318.560679] usb 2-4: generic converter now attached to ttyUSB0
[73318.601617] usbserial_generic 2-4:1.1: generic converter detected
[73318.601701] usb 2-4: generic converter now attached to ttyUSB1
```

This seems pretty good I at least have a device to point moto4lin at, however sadly moto4lin will still not connect to the phone.

I have come across a couple of posts that talk about cdc-acm module needing to be loaded before the usbserial module, and that once that is done /dev/acm0 or some such will show up under /dev/ and that will work with moto4lin. Unfortunatly I have know idea how one might get this to load first since usbserial is compiled into the kernel. Suppose I could compile my own kernel from source and make both usbserial, and cdc_acm modules. Anyhow, any ideas would be much appreciated.

Thanks
Yertman

---


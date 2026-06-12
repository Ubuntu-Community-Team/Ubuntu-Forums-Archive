---
title: "USBIR Tranciever... ACT-IR4010U"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by encompass on 2006-03-09
Actisys has given me an IR reciever to test as there new product.  I think it is working... I have the following results..
lsusb:
> Bus 003 Device 005: ID 066f:4210 SigmaTel, Inc.
after looking up the USB ID I got this site...
[http://www.dse.co.nz/isroot/dse/support/XH8286_Manual.pdf](http://www.dse.co.nz/isroot/dse/support/XH8286_Manual.pdf)
a quick look through there showed that this device does work with linux like the company told me.  it assigns itself to /dev/ttyUSB0
further looking got me this from the dmesg...
> jason@tabby:~$ dmesg | grep IR
[4333263.401000] IR Dongle ttyUSB0: IR Dongle converter now disconnected from ttyUSB0
[4333346.276000] ir-usb 3-4:1.0: IR Dongle converter detected
[4333346.279000] usb 3-4: IR Dongle converter now attached to ttyUSB0

so it looks like the driver is working properly...
But I want to use it to reciever information from an old remote I have.  That way I can use it to run my dvd player and music without getting up.  And we all know how lazy I am. ;)
BUT FROM THIS POINT... I am stumped as how to use it with a remote or anything else for that matter.  Where do I start... what do I do?
Any help would be appreciated...

---


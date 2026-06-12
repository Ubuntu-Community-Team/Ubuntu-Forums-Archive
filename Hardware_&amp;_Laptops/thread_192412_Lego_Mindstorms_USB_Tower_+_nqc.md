---
title: "Lego Mindstorms USB Tower + nqc"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by m0nstr42 on 2006-06-08
Has anyone had any luck getting lego mindstorms with the new(ish) usb IR tower to work in Ubuntu using nqc?

After searching around a bit I found the driver for the tower, modprobed it, and when I plug in the tower I get a green light blink, a /dev/legousbtower0, and some happy-sounding messages in dmesg:

```
[4893595.222000] drivers/usb/misc/legousbtower.c: LEGO USB Tower #0 now attached to major 180 minor 160
[4893595.226000] drivers/usb/misc/legousbtower.c: LEGO USB Tower firmware version is 1.0 build 134

```

However when I try to communicate with nqc I get the likes of:

```
 nqc -Susb -near (or any other command)
Could not open serial port or USB device
```

Any ideas?  sudo'ing the commands doesn't help either.

This *could* help:  at one point I found a claim that nqc wants to find the device at /dev/usb/leg0 or /dev/usb/lego0 or some such, so I tried ln -s /dev/legousbtower0 /dev/usb/leg0 etc, but this did not work either.  I'm not even sure how reliable that information is.

---


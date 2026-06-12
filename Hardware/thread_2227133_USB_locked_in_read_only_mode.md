---
title: "USB locked in read only mode"
date: 2014-05-30
forum: Hardware
---

### Post by SiL3NTK0D3R on 2014-05-30
Hi, So I wanted to transfer some files over from my HDD to usb, for which I needed to mount the USB. Transfer went complete and my laptop restarted randomly, without unmounting the usb.
Now the USB is stuck in write-protect mode. I tried several options to wipe the USB and change its permissions, but all of my steps were unsuccessful. 

The USB is Sandisk Cruzer Blade 32GB, with no write protection switch.

I used hdparm /dev/sdb1 to get the parameters of the USB and this is what comes up
```

SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 14 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 multcount     =  0 (off)
 readonly      =  1 (on)
 readahead     = 256 (on)
 geometry      = 30532/64/32, sectors = 62527488, start = 2048

```

Anyone other ideas anyone may have? 

Thanks

---


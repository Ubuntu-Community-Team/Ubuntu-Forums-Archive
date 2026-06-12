---
title: "mvox100"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by samkap23 on 2005-12-01
Hello,

I am trying to get an mvox100 speaker phone to work with Ubuntu Breezy.  It is a USB audio device ([http://www.mvox.com/mv100.html](http://www.mvox.com/mv100.html)).  When I plug it in, I expect to see a new device (such as /dev/dsp1) to appear.  Instead, nothing happens.

Here is what dmesg has to say:

```

[4295132.619000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[4295132.720000] invalid SELECTOR UNIT descriptor 7
[4295132.720000] snd-usb-audio: probe of 3-1:1.0 failed with error -5

```

So, the error seems to occur while loading 'snd-usb-audio'.

Any ideas?

Thanks in advance,

Sam

---

### Post by samkap23 on 2005-12-03
Some more information:

Under windows, this device does not require any mvox drivers.  I assume that the device is similar to a usb headset.  So, if anyone has experience with getting any usb audio device (eg. a headset) working in Ubuntu, that may be useful here.

Thanks,

Sam

---


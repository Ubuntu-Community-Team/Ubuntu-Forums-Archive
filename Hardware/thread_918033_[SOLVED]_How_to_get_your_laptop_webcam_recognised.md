---
title: "[SOLVED] How to get your laptop webcam recognised?"
date: 2008-09-12
forum: Hardware
---

### Post by minj on 2008-09-12
Is there anyone who actually got his integrated webcam recognised?

I have a customised ASUS Z37S. Asus doesn't provide the webcam model nor does it identify itself in ubuntu (tried both lspci and lshw). Any ideas?

---

### Post by minj on 2008-09-13
OK... So after a lot of forum reading I realised that this line in lsusb may refer to my camera:

```
Bus 007 Device 003: ID 05e3:0503 Genesys Logic, Inc. 
```

Very descriptive I know...

After some searching I found the appropriate manufacturer page:
[http://www.genesyslogic.com/_en/product.php?classid=7](http://www.genesyslogic.com/_en/product.php?classid=7)
It appears to come in 2 different flavours GL860 and GL860A. Since GL860A supports UVC and my cam doesn't, GL860 is the culprit.

After more searching I've found the driver (still in development)
[http://sourceforge.net/projects/gl860](http://sourceforge.net/projects/gl860)

Just download the sources untar and run ./install (see README for more details)

Appropriate bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215604](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215604)

It seems this driver will be included in the kernel as soon as it's perfected.

---

### Post by natrixnatrix89 on 2009-02-28
Hmm. I have a genesys webcam too, but it's code is
```
Bus 007 Device 003: ID 05e3:0505 Genesys Logic, Inc.
```
very similar to your.. I also can't get my integrated webcam to work. I downloaded the drivers from that page and installed them, but still the webcam doesn't work.. maybe I downloaded the wrong package? can anyone help please?

---


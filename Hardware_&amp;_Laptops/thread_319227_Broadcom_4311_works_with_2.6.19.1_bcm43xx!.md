---
title: "Broadcom 4311 works with 2.6.19.1 bcm43xx!"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by yarinb on 2006-12-15
--UPDATE: False alaram :( bcm43xx is not stable afterall... ](*,) sorry about that 

After a deep research, I've managed to make my DELL D820 work with Nvidia's driver and Broadcom 4311 wireless card without the famous ndiswrapper IRQ problem!

I just compiled 2.6.19.1 now and heavily tested the wireless connection together with NVIDIA's driver (downloading kernels over and over for 5 hours with OpenGL screensaver running altogether)

So far so good... anyone else here with broadcom bcm4311 cards, please test this as well. I used the built in bcm43xx driver with the firmware from:
```
/usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

this comes with package bcm43xx-fwcutter.

---

### Post by jan quark on 2007-12-20
Have a Dell Inspirion 1501 with Broadcom 4311 chip. I always manage to enable the firmware via fxcutter but after few reboots and some internet surfing the  bit rate drops to 1MBit (normal 24MBits). Dont really have a clue whats going on. Read almost all posts dealing with the Broadcom problem but to no avail. Will post here soon, making a fresh install of Gutsy on my laptop right now.

---

### Post by igknighted on 2007-12-20
The bcm43xx driver (the native one you are using) will report this.  If this is actually bottlenecking you then you could try using ndiswrapper, but unless you are on a connection faster than cable or transfer files over a lan, chances are this connection will not bottleneck you and should be fine as is.

---


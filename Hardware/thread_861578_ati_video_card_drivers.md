---
title: "ati video card drivers"
date: 2008-07-16
forum: Hardware
---

### Post by nnebular22 on 2008-07-16
I have the proprietary drivers enabled... still not working properly.  lags... a lot.  really.... A LOT

dell dimensio xps desktop
pentium 4 ht
2.8 Ghz
1GB ram
200GB SATA hard drive.

new install ubuntu 8.04

loading hardware drivers failed at boot time.

hardy previously worked fine on this machine.

how do i fix this problem?

---

### Post by nnebular22 on 2008-07-16
the graphics card is an ATI radeon 9800 pro.

any ideas

---

### Post by tuxxy on 2008-07-16
I just got rid of ATI and upgraded to nVidia, the drivers are so much better and also it runs faultlessly unlike the ATI.  

While I used ATI I had to put up with a few minor display issues eg not being able to run 3D!

```
glxinfo | grep 'OpenGL vendor'
```

Will show the driver in use

---


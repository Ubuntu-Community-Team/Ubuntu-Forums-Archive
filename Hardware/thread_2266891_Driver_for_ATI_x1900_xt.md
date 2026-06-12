---
title: "Driver for ATI x1900 xt"
date: 2015-02-26
forum: Hardware
---

### Post by turbo511 on 2015-02-26
i cant find the right graphics driver for my machine. i have an ati x1900 xt with a accelero x2 cooler. its replacing my old evga e-geforce 8600 gts.... but the problem is, i cant find working driver for the card. and all of the tutorials dont help much. it cant be found in additional drivers, and the x server one dont work at all. what should i do?

---

### Post by mörgæs on 2015-02-26
There is only one driver available for this card and that's the open source driver which is installed by default.

The drivers are rapidly improving and I recommend at least kernel 3.16.

---

### Post by Mark Phelps on 2015-02-26
Sorry, but AMD dropped Linux driver support for your card YEARS ago, and as morgaes indicated, the default Radeon driver is the one available now.  There are no drivers you can get from AMD that will work with your card and any recent version of Ubuntu.

---

### Post by Yellow Pasque on 2015-02-26
The real question is: what is wrong with the default driver? Does X not start? No 3D accel? Be more specific.
Also, did you have proprietary nvidia driver installed and completely remove it?

> There are no **proprietary** drivers you can get from AMD that will work with your card and any recent version of Ubuntu, **but you don't need proprietary drivers** 
Fixed.

---

### Post by Rob Sayer on 2015-02-26
According to this:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

the open source radeon driver should work fine, with 3D hardware acceleration.

As mentioned, that's the only working driver available.

---


---
title: "Kodak v570 camera not being recognized"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by jcruzlara on 2007-04-09
Hi I'm having problems with my kodak camera it's a v570 model and when I press the transfer button on the camera's dock Import Photos comes up but I get this error:


An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.



If I press the select camera model nothing happens. Please help I've searched google but found nothing to fix it.

---

### Post by St. Coin on 2007-04-09
You might try the fixes here:
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

I have tried them and they unfortunately do not work for me, but it seems like they work for the majority of people that have this problem.

- St. Coin

---

### Post by jcruzlara on 2007-04-09
You are amazing you rock. Second link worked thank you so much. :)

---


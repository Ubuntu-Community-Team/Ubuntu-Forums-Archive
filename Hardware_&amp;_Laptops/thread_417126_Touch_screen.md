---
title: "Touch screen"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by scalcave on 2007-04-21
I have a Panasonic cf-74 with a Fujitsu Takamisawa USB Touch Panel and I can not figure out how to set it up.  I have quadriplegia and it would really help if I could use the touch screen.  It is the the only thing holding me back in linux and any help would be appreciated!

---

### Post by idlewild on 2007-05-07
You need a Xorg evdev driver capable of absolute positioning. Have a look [here]("http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html"). You'll need kernel and xorg headers to compile. Calibration isn't much fun, hopefully someone will come up with a neat program to do it sometime.

---


---
title: "x800 Hoary?"
date: 2005-01-09
forum: Hardware &amp; Laptops
---

### Post by largo on 2005-01-09
Hi there

I'm trying to get the 3D acceleration on my x800 to work. The wary fglrx-driver is obviously to old. How must i edit my /etc/apt/sources.list to install  the new driver (someone said from a hoary server or something). Thanx for your answers

---

### Post by daniels on 2005-01-09
If you're using Hoary, you won't get 3D acceleration, because ATI have not yet publicly released a driver with support for newer cards that works with X.Org.  They do have one in beta, which will be released next week, and uploaded to hoary as soon as it's released.

---

### Post by largo on 2005-01-09
I'm not using hoary. I have warty installed, but the fglrx drivers on there do no support the x800

---

### Post by daniels on 2005-01-09
I don't think ATI had released a version of fglrx that worked with the X800 by the time Warty was out; in fact, I'm pretty sure they hadn't.

---

### Post by largo on 2005-01-09
I just went to the ati homepage and saw, that they have a driver for the x800. but its an rpm. I just have to convert it to a deb package now...

---


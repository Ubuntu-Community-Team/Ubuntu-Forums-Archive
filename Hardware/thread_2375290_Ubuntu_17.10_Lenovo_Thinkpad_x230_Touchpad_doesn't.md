---
title: "Ubuntu 17.10 Lenovo Thinkpad x230 Touchpad doesn't work well on Unity"
date: 2017-10-23
forum: Hardware
---

### Post by xabaom on 2017-10-23
Hi people.

I am unable to click touching directly on my touchpad.

Furthermore, I am unable to use the natural scrolling.

Take a look my "Mouse & Touchpad" panel on Ubuntu 17.10 with Unity (observe it is missing some options - considering Ubuntu 17.04):

[https://goo.gl/ZwUfvT](https://goo.gl/ZwUfvT)

I suppose this is a bug and I waiting some fixing in the next updates.

What do you (all) think about?

---

### Post by xabaom on 2017-10-23
SOLVED!

I discovered I need to install synaptics that it was not installed by default.
Reference: [https://askubuntu.com/questions/951084/thinkpad-x230-touchpad-scroll-momentum-inertial-scrolling-doesnt-work-how-to](https://askubuntu.com/questions/951084/thinkpad-x230-touchpad-scroll-momentum-inertial-scrolling-doesnt-work-how-to)

So, I suppose the hardware detection on installation it is not working really well on Ubuntu 17.10 for Lenovo Launchpad x230.   

So, to fix it, just install the synaptics support:

:$ sudo apt install xserver-xorg-input-synaptics

---

### Post by drnaseeb on 2018-02-23
> **xabaom said:**
> SOLVED!

:$ sudo apt install xserver-xorg-input-synaptics


Will it work for Asus X200MA?

---

### Post by drnaseeb on 2018-02-23
Excellent !!!
It worked.

---


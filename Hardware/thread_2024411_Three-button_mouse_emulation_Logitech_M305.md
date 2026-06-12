---
title: "Three-button mouse emulation: Logitech M305"
date: 2012-07-13
forum: Hardware
---

### Post by manthony121 on 2012-07-13
I am using a Logitech M305 wireless mouse with a computer running a fresh install of 12.04.  I cannot get 3-button emulation to work.  "dpkg -l" shows that "xserver-xorg-input-mouse" is installed, but I cannot find an X config file.  Should there be one?  The system is running the Unity (default) interface.

---

### Post by jmfal on 2012-07-13
Take a look at this.

[https://wiki.ubuntu.com/X/Config/](https://wiki.ubuntu.com/X/Config/)

You'll have to do some research if you re trying to reconfigure your mouse

---

### Post by manthony121 on 2013-03-21
Actually, this works just fine, and is much easier:

gpointing-device-settings

---

### Post by manthony121 on 2013-04-11
This works even better:

xinput --set-prop 8 265 1

---


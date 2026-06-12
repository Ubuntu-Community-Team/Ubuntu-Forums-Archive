---
title: "Adjusting screen resolution"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by geovino on 2007-05-02
I just bought a viewsonic 19" VA1912wb monitor from a friend and I also installed a Nvidia Geoforce FX5200 video card. It says that an optimum resolution is 1440x900. When I check screen resolution in Feisty it only goes up to 1024x768. How can I change this to a higher resolution. I was able to reset the resolution in PCLOS .92 which is also on this PC. How do I do I in Feisty?

Thanks

---

### Post by taurus on 2007-05-02
Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then <Ctrl><Alt>Backspace to restart X.

---

### Post by geovino on 2007-05-02
Thanks, it worked!

---

### Post by geovino on 2007-05-25
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then <Ctrl><Alt>Backspace to restart X.

I have Xubuntu on the same computer. The video seems ok except that the fonts aren't as sharp as in Ubuntu. Can I run this command in Xubuntu and see if it helps?

---


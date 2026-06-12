---
title: "Change in Monitor"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by lliberio on 2005-11-21
We were forced to change our monitor from a Samsung to a KDS. Now Ubuntu goes through the boot procedure and ends up with a blank screen and the monitor is sleep mode.

Obviously, it doesn't automatically adjust for the change.  How do I fix it?

We can't get to any graphical interface at this point, and I don't want to reinstall due to applications that have been installed.

All advice is appreciated.

Thanks, Lou..

---

### Post by Fittersman on 2005-11-23
hey man im goin through the same problem so if you can find an answer go to ubuntu forums -> ubuntu hoary hedgehog 5.04 -> hoary 5.04 application support -> other application support -> X server problem and help me out and if i firgure it out ill give it to you alright?

---

### Post by rjwood on 2005-11-23
```
sudo dpkg-reconfigure xserver-xorg
``` and when you get to the monitor portion tell it about your new monitor. Have your new manuel available for input.

---

### Post by Fittersman on 2005-11-23
hey man can you go to the place i stated earlier and check out my problem? its basically the same thing but it is slightly different.

---


---
title: "Processor and fan on HP 6125"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by Divni on 2006-11-22
Hi!

I've installed Ubuntu 6.06 on my laptop HP 6125 and every time when Ubuntu is running my fan is working at maximum speed and processor (AMD Turion mobile) is running always between 95% and 100% which slows down my system.

Is there something I could do to fix this?

---

### Post by alesdoc on 2006-12-17
noapci nolapic is the option for the kernel line that solves the processor's issue.

For the temperature's issue just install sensors-applet anche put it on the gnome-panel.

---


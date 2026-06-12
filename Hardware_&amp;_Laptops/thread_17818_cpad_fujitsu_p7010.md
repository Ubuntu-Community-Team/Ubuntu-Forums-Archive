---
title: "cpad? fujitsu p7010"
date: 2005-03-02
forum: Hardware &amp; Laptops
---

### Post by sunscape on 2005-03-02
Hey! I thought hoary was supposed to support the touchpad on my laptop? I have a fujitsu p7010 and it has a weird type of touchpad with a scroll button. The synaptics driver is good for nothing! in my case. (cpad?).. anyway, any info about this?


Yeah so, I edited the grub boot options to include i8042.nomux and presto! Scroll button and touchpad scroll works perfectly without any tuning. Plus the erratic pointer issue is gone.

Btw, later kernel releases might include this option as default. Hurray! or something.
Just happy it finally works, eh!

---

### Post by sinaen on 2006-05-11
[QUOTE=sunscape]Hey! I thought hoary was supposed to support the touchpad on my laptop? I have a fujitsu p7010 and it has a weird type of touchpad with a scroll button. The synaptics driver is good for nothing! in my case. (cpad?).. anyway, any info about this?


Yeah so, I edited the grub boot options to include i8042.nomux and presto! Scroll button and touchpad scroll works perfectly without any tuning. Plus the erratic pointer issue is gone.

Btw, later kernel releases might include this option as default. Hurray! or something.
Just happy it finally works, eh![/QUOTE]


Hey How did you get it to work so smoothly. my touchpad is going up but not down :) whats youre other settings?

---


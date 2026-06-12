---
title: "Gutsy Power"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by marcantonio on 2007-11-06
Hey all,

I recently upgraded from Feisty to Gutsy.  With Feisty my laptop batteries would last ~4.5 hours.  Since Gutsy I get about ~1.5 hours.  I have an HP nw8440.  Any suggestions?

Thanks,
Marc

---

### Post by dgar on 2007-11-06
There are some bugs relating to this which escape me.  I think there is something causing the hard drive to keep spinning up.  REgardless, try this:

sudo apt-get install powertop

sudo powertop

Then, every 4 seconds or so, it will list another 'recommendation' to save more power.

---


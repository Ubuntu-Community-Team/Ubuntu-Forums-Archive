---
title: "Choosing a DE"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by qalimas on 2006-02-20
I'm familiar with Xfce, KDE, and GNOME.  I don't care much for Xfce for all time use, however I've aquired a laptop for free from a customer.  It's a Athlon 2800+ with 184mb RAM.  Kubuntu runs ok on it, but I'd liek to know hte best DE to use for it's specs (the RAM is my concern).  I love KDE, and am partial to GNOME, should I just follow strict preference?

---

### Post by aysiu on 2006-02-20
The best would be XFCE.

If you're willing to not have a full desktop environment, you could try IceWM or Fluxbox, too.

If you really prefer KDE, try doing this: ```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` and then walk through the "wizard." At one point, you'll be asked about "effects,"--choose the minimal effects (I usually disable everything except for desktop wallpaper and image previews).

---


---
title: "How do I find out what my video is?"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by newbie22 on 2007-03-20
lspci says "VGA compatible controller: Intel Corp. 82810 CGC [Chipset Graphics Controller] (rev 03)"  So what does that make my onboard video?

---

### Post by taurus on 2007-03-20
You have an Intel onboard graphic controller 82810.  Therefore, you should be using "i810" driver in /etc/X11/xorg.conf.

---


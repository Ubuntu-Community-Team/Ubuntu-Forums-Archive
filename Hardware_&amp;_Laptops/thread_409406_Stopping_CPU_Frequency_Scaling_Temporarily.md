---
title: "Stopping CPU Frequency Scaling Temporarily"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by mthakur2006 on 2007-04-14
Hi,
Is there a way to stop CPU Frequency scaling temporarily (so that the CPU runs at full speed) when using a certain software e.g. VMWare?

I am using an Intel Celeron M Processor at 1.50 Ghz

Thanks,
M Thakur:popcorn:

---

### Post by mthakur2006 on 2007-04-14
anyone?

---

### Post by Zeroedout on 2007-04-14
> **mthakur2006 said:**
> Hi,
Is there a way to stop CPU Frequency scaling temporarily (so that the CPU runs at full speed) when using a certain software e.g. VMWare?

I am using an Intel Celeron M Processor at 1.50 Ghz

Thanks,
M Thakur:popcorn:

Click the cpu frequency applet and hit performance or powersave depending on your preferance? If you don't have the applet, right click a panel and hit add to panel, then find frequency scaling applet, if it doesn't give you the option, then go to a terminal and type sudo dpkg-reconfigure gnome-applets. It'll ask you if you want to install frequency selctor with suid or something to that effect, say yes.

---

### Post by mthakur2006 on 2007-04-15
thanx, that helped.

---


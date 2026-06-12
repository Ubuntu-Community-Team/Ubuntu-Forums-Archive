---
title: "nVidia Driver"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by jimmymac on 2006-11-23
Hi guys,

I just installed the nvidia driver from the nvidia website.  Rebooted machine and while I've still got a graphical display, it will only display in 1280x800.  No other choice!

Any ideas?

TIA

Jimmy

---

### Post by NotJustANewbie on 2006-11-23
I would have used the Ubuntu package "nvidia-glx" myself.
I accordance to your problem, I'd remove the website version and install that package and change the "nv" string in /etc/X11/xorg.conf to "nvidia"

---

### Post by jimmymac on 2006-11-23
OK I got the package down.

Two questions from a n00b!

1.  How do I remove the old driver?

2.  There isn't an 'nv' string in the xorg.conf file, what does this mean?

Cheers,

Jimmy

---

### Post by jimmymac on 2006-11-24
Ok update on this...

I restored the backup of my xorg.conf file.  Which (funnily enough!) has stopped the gui booting.  Now I can fix this by just installing Ubuntu again.

However, I would like to troubleshoot it just for the experience!

Could somebody point me in the right direction!

MTIA

Jimmy

---


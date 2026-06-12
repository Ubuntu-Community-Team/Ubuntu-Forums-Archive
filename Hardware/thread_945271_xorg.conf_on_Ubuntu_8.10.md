---
title: "xorg.conf on Ubuntu 8.10"
date: 2008-10-12
forum: Hardware
---

### Post by rmdnet on 2008-10-12
Hi!

I just installed Xubuntu 8.10 on a toshiba tecra 8000. I'm trying to edit the file /etc/X11/xorg.conf but it appears empty or at least just the generic one, without any configuration.
Is xorg.conf somewhere else on Ubuntu 8.10?. I can get just 800x600 resolution on my Tecra 8000.

Thanks!

---

### Post by kcnnc on 2008-11-05
Same question, where do we edit xorg.conf in 8.10? Just add to the file?

---

### Post by mgangav on 2008-11-05
It looks like Intrepid has reduced the dependency on the xorg.conf file. You may have to search for an alternate solution to your problem. 

Also, the xorg.conf file is at '/etc/X11/xorg.conf'. It now has only generic content.

---

### Post by fitzjohn on 2008-11-05
[Partial Solution]
I had the same problem using Ubuntu 8.10 on a Toshiba Tecra M1 with a Trident Microsystems CyberBlade XP4m32 (rev 91) video card.

My problem was solved by following this:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) and using "trident" for the driver name.

Unfortunately, the changes to my /etc/X11/xorg.conf did not persist after a restart of my system.

---


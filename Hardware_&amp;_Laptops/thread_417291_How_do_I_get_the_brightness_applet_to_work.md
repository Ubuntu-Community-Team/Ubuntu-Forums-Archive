---
title: "How do I get the brightness applet to work?"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by vicox on 2007-04-21
Hi,

the hotkeys to adjust the LCD brightness on my Sony VAIO Laptop work, but the brightness applet (Gnome) does not.

To get the CPU frequency and governor selector to work, i had to do:
```
sudo chmod 4755 /usr/bin/cpufreq-selector
```

but this doesen't do the trick here.

Anyone have an idea?

---

### Post by forrestgump on 2007-04-24
Bump

I have the same problem here (except can't even get fn keys to work) - anyone help?

---

### Post by kWahab on 2007-05-06
I had to blacklist the "video" module for my Dell Inspiron 6400. 
I followed this guide 
[http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)
All Fn keys work now.

---


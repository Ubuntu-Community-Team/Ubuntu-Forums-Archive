---
title: "Warning! /etc/modprobe.conf exists but does not include /etc/modprobe.d/!"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by matthew on 2005-07-01
All seems to be running great on my laptop, however I was watching it boot today and noticed the following error message:

Warning! /etc/modprobe.conf exists but does not include /etc/modprobe.d/!

I haven't made any changes recently so the warning has likely been there for over a month. That said, all is working quite well at the moment so this isn't a "I need help making something work" sort of issue. I'm more interested in what the message means and why it is coming up.

If anyone is interested in having me post the contents of my modprobe.conf file or list what is in the modprobe.d directory let me know and I'll do so.

---

### Post by Xian on 2005-07-01
I don't even have a /etc/modprobe.conf file on my system. :)
```
$ locate modprobe.conf
/usr/share/doc/module-init-tools/examples/generate-modprobe.conf.gz
/usr/share/man/man5/modprobe.conf.5.gz
```
But if I did, I would open it and add this line:
```
include /etc/modprobe.d/
```

---

### Post by matthew on 2005-07-01
That worked perfectly, thank you!

---


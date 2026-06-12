---
title: "Upgrade hosed my laptop"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by ripgut on 2008-01-06
Trying to remove xorg-driver-fglrx from my system to start over and i get the following error
[IMG]http://img153.imageshack.us/img153/6500/screenshotsynapticaw2.png[/IMG]

I've recently upgraded from 7.04 to 7.10 but somehow my ATI drivers  got screwed up, when i try to remove them via the terminal, i get

```
dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
  different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---


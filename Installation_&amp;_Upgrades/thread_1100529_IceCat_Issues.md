---
title: "IceCat Issues"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by jcolks on 2009-03-19
Hm - I'm relatively new to Ubuntu, a few months, but I thought I would be able to handle this one. However, after about 2 hours of searching, I'm having some issues with GTK2 and I am not able to figure them out. Maybe I can get some step-by-step assistance? Here's what I've got:

Installing icecat, I get to the ./configure step, when I am smacked with this error message:
```
checking for gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 gdk-x11-2.0 glib-2.0 gobject -2.0... Requested 'gtk+-2.0 >= 2.10.0' but version of GTK+ is 2.8.20 Package gtk +-unix-print-2.0 was not found in the pkg-config search path. Perhaps you should  add the directory containing `gtk+-unix-print-2.0.pc' to the PKG_CONFIG_PATH en vironment variable No package 'gtk+-unix-print-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 g dk-x11-2.0 glib-2.0 gobject-2.0) not met; consider adjusting the PKG_CONFIG_PATH  environment variable if your libraries are in a nonstandard prefix so pkg-confi g can find them.

```

Any ideas, folks? It tells me what I need right there, I just cannot find the script or package to get it movin

---

### Post by gentagelse on 2009-03-19
Looks like you are missing some packages. Have you updated your system? Unsure, just run
sudo apt-get update
sudo apt-get upgrade
In the Terminal.

---


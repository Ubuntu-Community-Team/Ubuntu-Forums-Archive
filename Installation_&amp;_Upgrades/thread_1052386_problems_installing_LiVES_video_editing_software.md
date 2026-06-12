---
title: "problems installing LiVES video editing software"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by Adali on 2009-01-27
I'm having trouble installing LiVES. During installation I got this output from the terminal:
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.4.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
___________________________________________________________________
How do I correct this issue???

---

### Post by Partyboi2 on 2009-01-27
Try installing the libgtk2.0-dev package
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by Iteria on 2009-05-29
Thanks that worked like a charm.

---


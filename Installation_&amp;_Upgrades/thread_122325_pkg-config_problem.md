---
title: "pkg-config problem"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by Reggie on 2006-01-27
Hi,

I'm trying to install gtk+ wich needs packages like pango. When I try to configure pango I get the following error:

```
*** 'pkg-config --modversion glib-2.0' returned 2.0.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```

I don't have /etc/ld.so.conf .. do I have to set PKG_CONFIG_PATH somewhere else ? Anyone knows where ?```

```

---


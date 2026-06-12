---
title: "broken gtk or libpangocairo?"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by mishkind on 2009-08-25
Hi,

The short story is I think I broke gtk or maybe just screwed up my libraries, and I want to get things working again.

The long story. I was trying to get flash working for 64 bitso I tried compiling a new version of swfdec from source, which required certain libraries (ie. libpangocairo, libpango1.0-dev, which required libcairo2-dev, which required....).
In the end I forced the version of some library (i dont rember but I'm pretty sure it was libgtk2.0-0), and I was able to compile swfdec, but then anything gtk related was broken.

Here is an example of something that doesn't work:


```
opus[~]$ gdebi-gtk 
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/gdebi-gtk", line 31, in <module>
    from GDebi.GDebi import GDebi
  File "/usr/lib/python2.5/site-packages/GDebi/GDebi.py", line 35, in <module>
    import gtk, gtk.glade
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libpangocairo-1.0.so.0: undefined symbol: pango_renderer_get_layout
```

So I think it is a libpangocairo error? I've tried anything obvious I could think of like uninstalling the libraries then reinstalling things including:

sudo apt-get remove gnome
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gnome

which I thought would cover everything but things still don't work. Any ideas aside from a re-install?

thanks,
mishkin

Ubuntu 8.04
x86_64
2.6.24-18-generic
libpango1.0-0 version 1.20.5-0ubuntu1.1
libpango1.0-common version 1.24.5-1
libcairo2 version 1.6.0-0ubuntu2
/usr/lib/libpangocairo-1.0.so.0 -> /usr/lib/libpangocairo-1.0.so.0.2002.3

---


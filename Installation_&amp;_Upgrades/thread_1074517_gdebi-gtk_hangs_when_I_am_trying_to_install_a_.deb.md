---
title: "gdebi-gtk hangs when I am trying to install a .deb using it"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by Moriak on 2009-02-19
Hi there, I had this problem for a couple of weeks now:

gdebi-gtk hangs when I am trying to install a .deb using it. Nothing is wrong when I user 'apt-get update' or 'apt-get updagrade' or 'dpkg -i *.deb'. It seems to install the package correctly but hangs for quite a while and I need to 'force quit' so it disapears. This is not a show stopper since I can use dpkg -i but it is an annoying. I did try with many different .deb files provided on developer sites (handbrake, virtual box, world of goo).

I am running 8.10 on a MacBook 2.1; I used the GUI update manager to upgrade from 8.04 (which was way more stable than the 8.10 version).

Anyone had this problem?

Here is the console output of gdebi-gtk. I did not found any verbose/debug swith so the output is not really detailled but there is that strange SSSSS string that is printed to the cosole.

```

raven@jr-macbook:~/Desktop$ gdebi-gtk
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.5/site-packages/GDebi/GDebi.py:100: GtkWarning: gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed
  self.window_main.set_sensitive(False)
/usr/lib/python2.5/site-packages/GDebi/GDebi.py:100: GtkWarning: gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed
  self.window_main.set_sensitive(False)
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS^C
raven@jr-macbook:~/Desktop$ gdebi-gtk
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.5/site-packages/GDebi/GDebi.py:100: GtkWarning: gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed
  self.window_main.set_sensitive(False)
/usr/lib/python2.5/site-packages/GDebi/GDebi.py:100: GtkWarning: gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed
  self.window_main.set_sensitive(False)
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS^C
raven@jr-macbook:~/Desktop$ 

```

---


---
title: "Upgrade to Intrepid Leaves GTK Apps Broken"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by tjbk_tjb on 2008-12-18
Whenever I attempt to run a GTK application, I get an error message like this:
```
$ thunderbird
/usr/lib/thunderbird/thunderbird-bin: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_new_class_handler
```
I've tried reinstalling the relevant package, libgtk2.0-0, with: ```
$ sudo aptitude reinstall libgtk2.0-0
```
That doesn't help.
Also, I ran the following:
```
$ strings /usr/lib/libgtk-x11-2.0.so.0|grep g_signal_new_class
g_signal_new_class_handler
```
So, it looks like the so-called undefined symbol exists in the library. It seems like some sort of linking error.
Does any one have any ideas?

---

### Post by tjbk_tjb on 2008-12-18
Never mind. For reference, the solution was:
```
$ sudo rm /usr/local/lib/libgobject-2.0.*
$ sudo ldconfig
```

---


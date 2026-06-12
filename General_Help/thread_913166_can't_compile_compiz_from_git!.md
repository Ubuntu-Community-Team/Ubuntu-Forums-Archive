---
title: "can't compile compiz from git!"
date: 2008-09-07
forum: General Help
---

### Post by chrisruls00 on 2008-09-07
I tried several scripts but none of them worked. So I tried using git myself and I keep getting errors! I can clone compiz bit when I try to "make" it I keep getting the same error. It looks like this:

```
make  all-recursive
make[1]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz'
Making all in include
make[2]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/include'
Making all in src
make[2]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/src'
Making all in libdecoration
make[2]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/libdecoration'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/libdecoration'
Making all in plugins
make[2]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/plugins'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/plugins'
Making all in images
make[2]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/images'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/images'
Making all in gtk
make[2]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/gtk'
Making all in window-decorator
make[3]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/gtk/window-decorator'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/gtk/window-decorator'
Making all in gnome
make[3]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/gtk/gnome'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/gtk/gnome'
make[3]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/gtk'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/gtk'
make[2]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/gtk'
Making all in kde
make[2]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/kde'
Making all in window-decorator
make[3]: Entering directory `/home/chrisruls00/compizplugins/scripts/compiz/kde/window-decorator'
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -I/usr/share/qt3/include -I/usr/include/kde    -g -O2 -Wall -D_FORTIFY_SOURCE=2 -MT decorator.moc.o -MD -MP -MF .deps/decorator.moc.Tpo -c -o decorator.moc.o decorator.moc.cpp
mv -f .deps/decorator.moc.Tpo .deps/decorator.moc.Po
/bin/moc window.h > window.moc.cpp
/bin/bash: /bin/moc: No such file or directory
make[3]: *** [window.moc.cpp] Error 127
make[3]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/kde/window-decorator'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz/kde'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chrisruls00/compizplugins/scripts/compiz'
make: *** [all] Error 2

```

It looks like the error happened in the /bin/bash: /bin/moc: No such file or directory part but I could be wrong. Anyone know how to fix this?

Edit:Ok I got it to work somehow... But now the focus and shade animations do not work.

---


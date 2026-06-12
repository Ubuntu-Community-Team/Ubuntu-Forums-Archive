---
title: "How to install newest version of gedit on hardy"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by Rockiger on 2009-03-25
Hello,

I would like to install the newest version of gedit on hardy without screwing my whole system.

How could I do it?

Here what I have done so far:

I installed glib-2.20 with "configure --prefix=/opt/glib"
then I tried to install gtk+-2.16, again with "configure --prefix=/opt/gtk".
Now I got the following error message:

```
In file included from gdk-pixbuf.h:41,
                 from gdk-pixbuf.c:31:
../gdk-pixbuf/gdk-pixbuf-enum-types.h:17:9: error: macro names must be identifiers
../gdk-pixbuf/gdk-pixbuf-enum-types.h:19:9: error: macro names must be identifiers
../gdk-pixbuf/gdk-pixbuf-enum-types.h:21:9: error: macro names must be identifiers
../gdk-pixbuf/gdk-pixbuf-enum-types.h:25:9: error: macro names must be identifiers
../gdk-pixbuf/gdk-pixbuf-enum-types.h:27:9: error: macro names must be identifiers
gdk-pixbuf.c: In function 'gdk_pixbuf_class_init':
gdk-pixbuf.c:101: error: 'GDK_TYPE_COLORSPACE' undeclared (first use in this function)
gdk-pixbuf.c:101: error: (Each undeclared identifier is reported only once
gdk-pixbuf.c:101: error: for each function it appears in.)

```

Any help on getting the newest gedit on hardy is appreciated.

Rockin' Regards,
Marco

---

### Post by meltunali on 2011-06-20
have you found the solution? i have exactly the same problem.

---


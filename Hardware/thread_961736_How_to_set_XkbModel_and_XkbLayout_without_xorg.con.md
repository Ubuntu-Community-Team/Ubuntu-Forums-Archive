---
title: "How to set XkbModel and XkbLayout without xorg.conf?"
date: 2008-10-28
forum: Hardware
---

### Post by monti on 2008-10-28
Hi.

I've upgraded to 8.10, and the Xorg works without an /etc/X11/xorg.conf now.  Except one thing:

I have a Kohjinsha SH6 netbook with a japanese keyboard, but use norwegian keyboard layout.  I did this earlier with a custom xkb symbol file (/etc/X11/xkb/symbols/no_jp) with the following content:

```
xkb_symbols "basic" {
   include "no(basic)"
   name[Group1]="Norway - japanese keyboard";

   // AltGr on Space's right side
   key <XFER> {
     type[Group1]="ONE_LEVEL",
     symbols[Group1] = [ ISO_Level3_Shift ]
   };
};

```
In xorg.conf, XkbModel was set to jp106 and XkbLayout to no_jp.

This doesn't work anymore.  I've moved "no_jp" to the new symbols dir /usr/share/X11/xkb/symbols/, but I don't really know where to set XkbModel and XkbLayout anymore.  Should the graphical keyboard preferences work=

(I previously moved my setup from xmodmap to xkb: [http://ubuntuforums.org/showthread.php?t=791442](http://ubuntuforums.org/showthread.php?t=791442) / [http://lists.freedesktop.org/archives/xorg/2008-May/035154.html](http://lists.freedesktop.org/archives/xorg/2008-May/035154.html) .  I thought I was future-proof, but I guess I was wrong...)

---


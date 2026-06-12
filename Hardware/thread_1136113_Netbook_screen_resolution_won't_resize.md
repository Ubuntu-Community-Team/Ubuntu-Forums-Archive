---
title: "Netbook screen resolution won't resize"
date: 2009-04-24
forum: Hardware
---

### Post by zadok the priest on 2009-04-24
Hi,
Please I need help, I'm at my wits end
I have an Advent 4213 netbook and I just installed 9.04 remix
I used it for about 4 hours then switched to the classic Ubuntu theme. I then shut down my netbook but on rebooting, the resolution has changed and its now too big
I don't know how to fix it, I've tried everything within my power to no avail. Any advice or tips please?
My VGA controller is an intel Mobile 945GME Integrated Graphics Controller.

---

### Post by KhurramM on 2009-04-26
READ:
man xrandr

then use:

xrandr -q
to display possible displays

select the one you need and:

xrandr -s 800x600 -r 75

where:
-s 800x600 are supposed to be your decided values
-r 75 are supposed to be your decided values

CAUTION: but only select the ones from xrandr -q

Hope this solves your problem.

DISCLAIMER:
===========
But I take no responsibility or whatsoever LOSS at your end.
use with caution.

---


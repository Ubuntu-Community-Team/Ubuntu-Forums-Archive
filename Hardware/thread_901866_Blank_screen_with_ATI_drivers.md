---
title: "Blank screen with ATI drivers"
date: 2008-08-26
forum: Hardware
---

### Post by ghoster on 2008-08-26
I'm trying to set up ATi drivers in hardy heron using [these]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") instructions, which seems to go well.
However, when I start X, the display goes blank. I can still log in, hear sound etc, just no image.

lspci shows two graphics cards; one a generic vesa and the other the ATI card, even though I only have the one card and no onboard graphics.

xorg.conf has two sets of graphics cards, monitors, and screens, even though I only have one of each.

fglrxinfo returns an error, stating that it can't find the monitor (null).

Any ideas on how to fix this?

---

### Post by Crafty Kisses on 2008-08-26
Have you tried reconfiguring X?

---

### Post by ghoster on 2008-08-26
Yep I've tried reconfiguring X.
Whenever I try anything automated, eg booting in recovery mode and trying to automatically fix X, I end up with two displays and two graphics cards list in xorg.conf.

---


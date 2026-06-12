---
title: "Dapper broke my Tablet"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by tiglionabbit on 2006-06-03
I have an Acer C300 Tablet PC.  In Breezy, I had it set up to work pretty decently with pressure sensitivity and all, by grabbing the wacom packages and editing xorg.conf.  It did still choose its max pressure value somewhat randomly though.

I just dist-upgraded to Dapper.  Now, just bringing my stylus into proximity causes xidump to crash with a Floating Point Exception.  If I use KDE, it kills the window manager instantly--  window contents stay interactive but their borders and the taskbars disappear making things unusable.

Other than that everything's working fine.  I read [the new wiki page on tablets]("https://wiki.ubuntu.com/Wacom"), but mine is serial, not USB.  What has changed between Breezy and Dapper on how Tablet PCs are handled, and what should I do to fix this?

---

### Post by chuvisco on 2006-06-07
I don't know why things would be crashing on you, but here's what I had to do after upgrading.  If I remember right, I had to change "/dev/ttyS0" in xorg.conf to "/dev/ttyS4".  You can do (sudo?) cat /dev/ttySX, replacing the X with 0, 1, 2, until you find the right one (touch your stylus to the screen and see which one gives you output).

---

### Post by nolongerlivecd on 2006-06-08
(not helpful, off-topic)... But it does give him output... the output is a screwy system

---


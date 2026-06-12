---
title: "Mouse help!"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by kylefarlow on 2006-04-02
The mouse built into my laptop is FUBAR and I must disable it.  It makes the cursor go crazy and I am not able to click on anything.

I want to use an external USB mouse instead.

So how can I disable the mouse (trackpad/point stick) built into my laptop without disabling external USB mice?  If I disable /dev/input/mice in xorg.conf, X won't start.

Please help!

---

### Post by Sef on 2006-04-02
I have the same problem with my laptop.  I hope someone answers your post who knows how to fix this issue.

---

### Post by kawack on 2006-04-20
What I did to disable the touchpad was to edit file:

/etx/X11/xorg.conf

find section "InputDevice"

and change option "SendCoreEvents" from true to false:

Option		"SendCoreEvents"	"false"

I hope it helps.

---


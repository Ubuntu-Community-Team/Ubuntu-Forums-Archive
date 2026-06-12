---
title: "Can't get all buttons working on MX1000 mouse in fiesty"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by Bazirker on 2007-04-23
I'm a recently converted windows/litestep user, and I had bunches of hotkeys set for my Logitech MX1000.  I can't get them working in fiesty and it's driving me insane!

I followed this, for edgy, cause there aren't instructions for fiesty yet:  [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

For some reason, making the changes in xorg.conf changes the mouse behavior but also resets the keyboard layout to evdev-managed and I have to go change it back.  Curiosly, the forward/back buttons now work in firefox but only if I hold shift.  My guess is something is wrong with the xbindkeys setup, but I have .xbindkeysrc in with my home folder and everything.  Anyone have any guesses?  Here's my xbindkeysrc file:

```
"/usr/bin/xvkbd -xsendevent -text "\[Shift_L]\[Left]""
  b:6
"/usr/bin/xvkbd -xsendevent -text "\[Shift_L]\[Right]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Right]""
  b:10
"echo ButtonRelease 11 ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonRelease 12 ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonRelease 13 ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonRelease 14 ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
```

---

### Post by hed on 2007-04-25
I have the same problem. The button 10 is not detected, and the backward and forward buttons only works if I hold shift.
Anyone has idea of how to solve this?
Is a bug of evdev?

---

### Post by bluehue on 2007-04-29
Yup,I have the problem as well :(

Edit: And now it decided to start working again after I don't know how many days :confused:

---


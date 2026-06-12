---
title: "Middle mouse button"
date: 2004-12-28
forum: Hardware &amp; Laptops
---

### Post by steverukuts on 2004-12-28
I've noticed that in Ubuntu, the middle mouse button is actually being sent as "mouse 3", like in windows, so that it is possible to close tabs in firefox by middleclicking on them. By default in most other distros, middleclicking pastes what's on the clipboard.

I need to replicate this behaviour on my laptop which does not run ubuntu (but does run kernel 2.6.10). Could someone recommend to me the changes I need to make to my xorg/xfree configuration or my system in general?

Thanks.

Steve.

---

### Post by diebels on 2004-12-28
middle mouse button does paste the clipboard in ubuntu, so I guess it's a firefox version issue.

---

### Post by mayco on 2004-12-28
[QUOTE=steverukuts]I've noticed that in Ubuntu, the middle mouse button is actually being sent as "mouse 3", like in windows, so that it is possible to close tabs in firefox by middleclicking on them. By default in most other distros, middleclicking pastes what's on the clipboard.

I need to replicate this behaviour on my laptop which does not run ubuntu (but does run kernel 2.6.10). Could someone recommend to me the changes I need to make to my xorg/xfree configuration or my system in general?

Thanks.

Steve.[/QUOTE]
in firefox: go to about:config 
in filter, type mouse
double click on middlemouse.contentLoadURL so it says false and becomes black
middleclicking on the tabs now works

i know, it should be default behavior in firefox under linux, but who am i to say that :)

---


---
title: "synaptic touchpad"
date: 2010-01-18
forum: Hardware
---

### Post by odm4286 on 2010-01-18
ok guys just bought a brand new hp netbook mini 210....everything works great except my touchpad. I can't get the buttons to work so i can't drag or right click

---

### Post by dgoosens on 2010-01-18
maybe btnx will be able to help you out...
[http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)

---

### Post by JCasper on 2010-01-20
I don't want to hijack your thread, but what wireless card did you get and was the driver already installed in ubuntu?

---

### Post by pi/roman on 2010-01-20
You may be able to get it working with synclient in a terminal.
for a terminal use alt/F2 then type xterm, then try:
synclient -l

which shuld bring up a list of options, then type:
synclient option*=value*

for example:
synclient touchpadoff=0

may be needed to enable it.

---


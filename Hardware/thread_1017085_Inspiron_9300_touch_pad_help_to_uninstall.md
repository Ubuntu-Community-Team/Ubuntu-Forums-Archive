---
title: "Inspiron 9300 touch pad help to uninstall"
date: 2008-12-20
forum: Hardware
---

### Post by snouy on 2008-12-20
Hi,

Really love ubuntu, have a small problem my touch pad and buttons on my inspiron 9300 they are stuck and give me random clicks and inputs.  i use my laptop as my desktop and use a USB mouse and key board that works great, i just want to uninstall or remove the mouse pad and buttons but have no clue how to go about this any help would be much appreciated.

---

### Post by Andy on 2009-02-24
wow same issue with my dell inspiron 9300 too

what ive done is turned off the pad and buttons completely and now use an external mouse

so if you want to do the same do this 

sudo rmmod psmouse

will kill the touchpad and buttons but not any new mice you plugin.

i used to dual boot windows and linux but now its all linux on that machine because there's no rmmod command and the mouse click goes apeshit

---


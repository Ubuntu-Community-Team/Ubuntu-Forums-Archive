---
title: "Logitech LX7 Mouse - Tilt wheel config"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by mrdeeno on 2007-01-01
I used these [instructions]("http://www.ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mouse") to get my forward and backward buttons to work on my Logitech LX7 cordless mouse.

I changed the buttons in my xbindkeysrc to read:
```
#Back Button
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8

#Forward Button
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

#Right scroll
"/usr/bin/xvkbd -xsendevent -text "\[Right]""
   m:0x0 + b:6

#Left Scroll
"/usr/bin/xvkbd -xsendevent -text "\[Left]""
   m:0x0 + b:7
```

My back and forward buttons work (8 and 7), but my lift and right tilt wheel (6 and 7) also goes back and forward rather than scrolling left or right.  

Anyone know if I have the code correct?

---

### Post by K.Mandla on 2007-01-05
(Moved to Hardware and Laptops. ;) )

---

### Post by fela on 2008-04-14
I have the same problem with the same mouse.

---


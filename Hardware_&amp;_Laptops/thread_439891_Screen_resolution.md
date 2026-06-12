---
title: "Screen resolution"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by run2siddharth on 2007-05-11
hi,

   i installed ubuntu 6.06 on my ibm thinpad t60p wide screen laptop...the graphics card is ATI mobility firegl v5250..the maximum resolution i am getting on ubuntu is 1024x768 while my laptop can have 1680x1050..i tried with frglx drivers but it didn't work..currently ubuntu is using vesa for display...please anybody can give me an insight of how to get it work..


Siddarth

---

### Post by renzokuken on 2007-05-11
could you post the contents of your xorg.cong

```
gksudo gedit /etc/X11/xorg.conf
```

and cpy and paste everything here

also, how did you install the fglrx driver? vesa only supports up to 1024x768 so you need the fglrx to go higher

---


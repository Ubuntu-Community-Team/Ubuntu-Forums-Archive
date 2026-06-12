---
title: "Aspire one 532h touchpad problems in Lucid Lunx (10.04)"
date: 2010-04-30
forum: Hardware
---

### Post by sharan.kevryn on 2010-04-30
Installed ubuntu 10.04 netbook remix on my aspire one 532h netbook. My touch pads vertical scroll doesnt work although i've enabled it in the mouse preferences. And is there a way to get the multi gesture feature to work in ubuntu?

---

### Post by BaroqueBloke on 2010-05-01
Unfortunately the side scroll bar does not work yet in 10.04.  I had been running the release candidate for a time and it was broken then, although it worked in 9.10.  

As far as multi touch goes I have been unable to find any fix for that.  Its the only thing from the Win7 starter that I was happy with.  

I will continue to search for a solution and will post here should I find one.  

good luck!

---

### Post by spiralx on 2010-05-03
...and continuing with that, it's now May 2010 - a while since the RC! -  and the problem has yet to be sorted out!

---

### Post by nnelG on 2010-05-15
Easy fix

1 - run ```
gksu gedit /etc/modprobe.d/psmouse.conf
```
2 - add ```
options psmouse proto=imps
```
3 - save
4 - reboot

Note:  The file doesn't exist but by doing the previous steps you will create the file and it will be loaded when you reboot.

Hope this helps!

---


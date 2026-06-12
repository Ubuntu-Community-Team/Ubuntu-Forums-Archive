---
title: "Changing motherboard"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by xMaximex on 2005-04-28
Hi,

I'll change my motherboard soon and I want to know if I can still use my current installation of Ubuntu with my new MB ? If yes, can I transfer the system from a hard drive to another ?? Windows is installed on a 120go HD and Ubuntu on a 20go and I want to switch Ubuntu on the 120go ... Can I do that ?

---

### Post by ignavia on 2005-04-28
[QUOTE=xMaximex]Hi,

I'll change my motherboard soon and I want to know if I can still use my current installation of Ubuntu with my new MB ? If yes, can I transfer the system from a hard drive to another ?? Windows is installed on a 120go HD and Ubuntu on a 20go and I want to switch Ubuntu on the 120go ... Can I do that ?[/QUOTE]
 This isn't an answer, but just to let you know, (I'm guessing you speak French, judging by your use of "go") in English it's gb for gigabyte, and since mb is megabyte, we usually say mobo for motherboard. 

I'm really not trying to be a jerk, I just wanted to let you know.

---

### Post by xMaximex on 2005-04-28
Okay ...

---

### Post by alastair on 2005-04-28
It should work OK again - but if the motherboard is /very/ different, you might see some problems with some devices. Hopefully, /most/ chipsets and devices are already supported by your Ubuntu install (there are a lot of modules under /lib/modules for all sorts of devices). 

So, you should be OK - but might have a problem if the new hardware is very different.

---

### Post by xMaximex on 2005-04-28
It will not be the same chipset .. now it's VIA and it will be nforce3 or 2 i dont remember

---

### Post by NaplesBill on 2005-04-28
I switched from a PIII/Celeron board to a Via based AMD board and didn't have any problems with the chipset.  I did have to change my xorg.conf because I'm using the IGP graphics on the motherboard.

---


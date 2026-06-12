---
title: "spindown the harddisk"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by ganssie on 2009-03-06
hello,

First i install ubunto (desktop 8.10) on a laptop and i can remember that 
when the connected usb drives where idle they spin down !

Now the laptop is broken :-( and i install ubuntu desktop on a desktop pc
but the usb disk are running for 24/7.



or is it possible to make a wake up event from the nic ?
when te system goes to sleep the drives spindown, but the only way to 
get it awake is move the mouse or press a key on the key board.

pleas help me a am en new to ubuntu/linux

---

### Post by khelben1979 on 2009-03-06
I don't understand exactly what you're after here. Maybe [hdparm]("http://en.wikipedia.org/wiki/Hdparm") is the thing you're looking for. See wiki link.

---

### Post by ganssie on 2009-03-06
thank you for your time ....
ok, ik want to spindown my USB harddisk when the have nothing to do.

works hdparm on USB harddisk ?

---

### Post by khelben1979 on 2009-03-06
I don't know, but you can try. The documentation says that you need to be careful about what parameters you decide to use so you won't destroy the data on the harddisk, which apparently can happen if being misused.

---


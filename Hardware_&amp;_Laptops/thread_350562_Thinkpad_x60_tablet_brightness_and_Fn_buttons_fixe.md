---
title: "Thinkpad x60 tablet brightness and Fn buttons fixed!"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by ecoxmit on 2007-01-31
For those with a Lenovo X60 tablet. 

After installing edgy, the brightness buttons (Fn + Home/Down) do not work (and in my case they actually froze the computer)

To fix this, just add "blacklist video" to the file /etc/modprobe.d/blacklist 

This was recommended as a fix for similar issues with Dell computers, but it works as well for the x60.

---

### Post by honeysucker on 2007-02-13
thanks,  fix my problem with my x60 :-)

---

### Post by freund on 2007-05-15
Thanks!
It work for me also!

---

### Post by lobner on 2007-06-04
Yes it works, but it has a somewhat slow reaction. Any clue on how to fix this?

Also, my screen often changes/adjusts the brightness by it self. Or rather it makes a quick shift in the brightness setting, and shows the brightness up/down indicator on the display.
I have been searching for a solution for this as well, but no luck. Does anyone know?

--lobner

---

### Post by oofnik on 2007-08-22
> **lobner said:**
> Yes it works, but it has a somewhat slow reaction. Any clue on how to fix this?

Nope, but it happens to me too. It's not real bad though. Better than blank screen right? :)

---


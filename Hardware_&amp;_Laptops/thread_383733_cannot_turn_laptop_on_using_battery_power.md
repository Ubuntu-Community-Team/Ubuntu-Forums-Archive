---
title: "cannot turn laptop on using battery power"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by thinman1189 on 2007-03-13
Hello. I have a dell inspiron 2200 running edgy eft. For some reason I cannot turn my laptop on unless the ac adapter is plugged in. The battery works after the laptop is turned on. Is this a setting issue or hardware issue? What can I do to fix it?

---

### Post by bernied on 2007-03-13
If the power doesn't come on at all then this is nothing to do with the operating system. I don't really know how laptops work at that level, but it sounds like hardware to me.

---

### Post by thinman1189 on 2007-03-13
what happens exactly is that it goes through the grub loading screen, then when it starts booting into ubuntu I can get through about 4 and 1/3 of the orange bars, and thats where it stays. When I use my other hard drive with XP it boots no problem on battery.

---

### Post by jolger on 2007-03-13
try alt+f1 as soon as the ubuntu boot screen appears... if you see something like "cpu-soft lock detected" (i cant remember if it was exactly that) then its (probably?) because of that... i had that on my laptop too (wich is in for repairs atm (but because of other issues))

anyways, if its the case that you get that message with cpu soft lock thingy... then it might be caused by that... unfortunately i have no other solution to this than just restart... (press and hold power button until it turns off and then turn it on again)



P.S. to any (really?) experienced linux user, is it normal that there would come something like "cpu-soft lock detected, bug xxxxxxx" <- not the exact phrase!

---

### Post by bernied on 2007-03-13
If you want to know what's going on, select your ubuntu at the grub menu (but don't hit Enter), then hit 'e' (for edit), then edit the entry, getting rid of the 'quiet' and 'splash' options in the 'kernel' line. There may be a line on its own with quiet in it, get rid of that too. Then hit 'b' (boot) and try to see where it goes wrong.

This will give you screenfuls of text and it might be difficult to see what the critical bit is, especially if it reboots. But if yours is just hanging, it should tell you what is going on. Just write down the last couple of lines (or take a pic if you have a digital camera) and we'll see where we get from there.

---


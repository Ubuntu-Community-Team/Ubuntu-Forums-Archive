---
title: "Keyboard Problem"
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by IndirectX on 2006-02-12
I've got a new installation of Ubuntu onto my desktop, an AMD system.  I'm using a Logitech Elite Keyboard.

The problem is that when I'm typing, it is as if a key gets stuck for a few seconds.  It pauses while I'm typing for maybe .5-1s, then it repeats a key perhaps 25 times (this is especially annoying if the key happens to be backspace).  I turned off key repeat hoping it would remedy the problem, but it only seemed to remedy the repeating part of the problem - it still seems to get stuck as though a key were being held down.

Has any one else encountered this?

---

### Post by Pilsner on 2006-05-28
I also have this problem as IndirectX.
I have also turned of key repeat as IndirectX.

The problem is still with that PAUSING and 3 seconds and so.. Pretty annoying.

Any solution?

---

### Post by hardcoreprawn on 2006-06-14
I have a similar problem on my T22 Laptop. When I first loaded Ubuntu up, it used to repeat (makes passwords tricky) keys, sometimes 1-2 extra, sometimes 6+. When I disabled Key repeats it stopped, but now, I can't scroll with cursors or delete many characters easily just on Keyboard. Anyone got any pointers as to what could be broken to sort this? I tried 3-4 different ubuntu's and the only one that never had the problem was a 2.4 kernel.

---

### Post by k225yt on 2006-06-15
Oh, yes. I have the same. 
[http://www.ubuntuforums.org/showthread.php?t=195069](http://www.ubuntuforums.org/showthread.php?t=195069)

---

### Post by bierpullen on 2006-06-15
i have the same problem on my acer aspire 1522. I use dapper since some time now.I have this problem voor 5 weeks.
:sad: :sad: :sad: 


----------------------------------------
Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php](http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php)

---

### Post by dmizer on 2006-06-16
if you do dmesg, is it overflowing with this:
```
[4335062.871000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4335063.546000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
```
if so, try the fix(s) in this thread: [http://www.ubuntuforums.org/showthread.php?t=119449&highlight=setkeycodes](http://www.ubuntuforums.org/showthread.php?t=119449&highlight=setkeycodes)

note: be sure to read through more than the first few posts as some of the links are dead, but there are updates.

---

### Post by bierpullen on 2006-06-20
Hi dmizer

The problem is fix't see this link [http://www.ubuntuforums.org/showthread.php?t=191945&highlight=keyboard+repeat](http://www.ubuntuforums.org/showthread.php?t=191945&highlight=keyboard+repeat)

=D> =D> =D> 

Thanks.


----------------------------------------
Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/acer_aspire.php](http://www.antarctica-rbak.nl/acer_aspire.php)

---


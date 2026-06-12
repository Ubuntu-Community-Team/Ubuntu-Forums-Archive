---
title: "Hangs during install"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by archer75 on 2005-12-08
Boot Screen comes up, I hit enter and alot of text begins to scroll on the screen. It hangs at various spots here. But it seems to start up my USB webcam and the lights come on my USB keyboard and then nothing. Completely locked up.

Does it not like USB hubs? I have had Ubuntu installed on this same computer before.
I do have 3 hard drives. 2 in Raid 0 on the motherboard Intel controller. Would that matter?

---

### Post by archer75 on 2005-12-09
It tends to hang at these two spots:

..TIMER: vector=0x31 pin1=2 pin2=-1

or 

isapnp:Scanning for PnP cards...

I have tried numerous boot options with no luck.

---

### Post by archer75 on 2005-12-09
Ok, I removed the RAID setup I had and now it's just single drives. Nothings changed for the Ubuntu install. Still hangs.

I tried and old beta disk 5.10 and same thing.

Tried Mandrake 10.0 and it works fine.

---

### Post by markcaetano@gmail.com on 2005-12-09
hi archer 
can u look at my problem cos it seems that u seem to no what ur are doing 
it is the one that says

CANT Start partitioner help
by [email]markcaetano@gmail.com[/email]

thanx mark
(P.S can u tell me what RAID is im not completly sure)

---

### Post by arnieboy on 2005-12-10
[QUOTE=archer75]Boot Screen comes up, I hit enter and alot of text begins to scroll on the screen. It hangs at various spots here. But it seems to start up my USB webcam and the lights come on my USB keyboard and then nothing. Completely locked up.

Does it not like USB hubs? I have had Ubuntu installed on this same computer before.
I do have 3 hard drives. 2 in Raid 0 on the motherboard Intel controller. Would that matter?[/QUOTE]
follow this howto:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

### Post by archer75 on 2005-12-11
[QUOTE=arnieboy]follow this howto:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)[/QUOTE]

It seems I would have to have Ubuntu installed to use this link, which is the problem, it won't install.

---

### Post by archer75 on 2005-12-11
Well I found the problem. Ubuntu will not install, or at least get past the initial screens with one of my USB hubs plugged in. Specifically a iogear 6 port USB hub and card reader.
Ubuntu seems to have no problem with the 4 port hub on my monitor.

---


---
title: "Yet another USB mp3 player problem."
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by z-vet on 2006-04-13
Hi all. 
I have problems copying files to my mp3 player (Sandisk Sansa e140): transfers are stalled. When i start copying it does really fast at first, but then it slows down and stops, showing errors like "Unable to copy...", but sometimes it works OK: player shows "USB Writing Data" message again and it copies. I tried amaroK's built-in media device manager, Krusader, MC, 'cp' command in shell...sometimes it works and sometimes doesn't, and i can't find what the problem is.  ](*,).

---

### Post by localzuk on 2006-04-13
Have you tried using another computer? Do these symptoms persist there also?

---

### Post by z-vet on 2006-04-13
[QUOTE=localzuk]Have you tried using another computer? Do these symptoms persist there also?[/QUOTE]
Not yet, i have to, but the second machine is occupied right now. Will try and report later.

---

### Post by z-vet on 2006-04-15
Hmmm... Two days of googling and it looks like a kernel bug. I'm not completely sure, but after reading [this](http://bugme.osdl.org/show_bug.cgi?id=4057) i did 
```
rmmod ehci_hcd
```
and transfers are OK: even if it shows "stalled" for some time, it transfers  after all (at least, for now). 
Comments, anyone?
Correction: after googling even more, i start to think it's something wrong with my hardware (USB controller or ports, maybe). My second machine is still occupied (internet addicts in action :-D). Will test it later...

---


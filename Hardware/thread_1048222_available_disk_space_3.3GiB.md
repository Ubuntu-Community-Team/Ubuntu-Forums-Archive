---
title: "available disk space: 3.3GiB ??"
date: 2009-01-23
forum: Hardware
---

### Post by chinmaya_n on 2009-01-23
when i checked "System Monitor" ...... It showed Memory as 3.9GiB and available disk space as 3.3GiB..... Why it is showing like that ???
Where does the ramaining 0.6GiB has gone???
___________ 
I'm using 8.10 -> intrepid.... and my RAM is 4.0 GiB.
plz anyone help !!

---

### Post by glotz on 2009-01-23
Uhm, because memory and disk space are different things?  (Of course, there are RAM disks and swaps and caches...)

---

### Post by Kevbert on 2009-01-23
What do you get if you go to terminal and type
```
free -m
```?

---

### Post by chinmaya_n on 2009-01-24
This was the output:
____________________________________________________________
```
[COLOR="Green"]
              total       used       free     shared    buffers     cached
Mem:          3950       3782        167          0       1551       1417
-/+ buffers/cache:        814       3135
Swap:         2611          5       2606[/COLOR
```

---

### Post by chinmaya_n on 2009-01-24
Is my system showing 4GB ram??? from the output i posted in above thread.
and is it using 4GB efficiently???

---

### Post by Kevbert on 2009-01-24
That output is fine. My PC shows 3.956GiB for 4Gb installed.  Your swap size is a little low if you want to use suspend and hibernate (it should be at least the same size as your RAM).

---

### Post by chinmaya_n on 2009-01-27
but in my system hybernate and suspend options are working properly........ will that cause any problem in future .......!!!

---


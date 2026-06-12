---
title: "How could i find out my motherboard brand and name with ubuntu?"
date: 2008-05-06
forum: Hardware
---

### Post by nick09 on 2008-05-06
I'm gonna get some new RAM for my mom(mom's present for upcoming sunday) and I need to know what brand the motherboard is.

---

### Post by Rocket2DMn on 2008-05-06
Try running
```
sudo lshw
```
That will list off all sorts of information about your hardware, hopefully a useful name will be given under *-core for your motherboard, but you can also look at BIOS and RAM info, among many other things.

---

### Post by nick09 on 2008-05-06
Thanks, sadly the RAM I was looking at can't run on the pc. 
But I found some RAM that works.
I can't wait until I can get this for mom.:)

RAM:
[http://www.amazon.com/Crucial-Technology-184-Pin-PC2700-333Mhz/dp/B0002IP2TY/ref=sr_1_2?ie=UTF8&s=pc&qid=1210117835&sr=1-2](http://www.amazon.com/Crucial-Technology-184-Pin-PC2700-333Mhz/dp/B0002IP2TY/ref=sr_1_2?ie=UTF8&s=pc&qid=1210117835&sr=1-2)

---

### Post by Jose Catre-Vandis on 2008-05-06
Or
```
sudo dmidecode
```
which gives some detailed info about motherboard, CPU and RAM

---


---
title: "Ati Card"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by lordb on 2006-12-29
:confused:  Hey all ... sorry if its been asked before but this is really bugging me .... i have a ATI graphics card ... well its Graphics By Ati ... which i read up on is manufactured by others but with ATI pieces ..... i cannot locate the drivers for it and my pc isnt reconising it either ... yet my old Pc did =S is there any way of finding out what drivers i need ??? any help would be much much appreciated !! 

/lordb

if it helps im runnin on a AMD XP2000 motherboard !!

---

### Post by pay on 2006-12-30
The drivers for it should be compilled into the kernel. What is the exact model of the card?```
sudo lspci | grep AGP #assuming agp card
```

---

### Post by lordb on 2006-12-30
im not exactly sure lol :S i have the serial number but how would i use that 2 find out wat card it is  it says

S/N H0503214914

sticker below it

R98-e-SD3B
barcode thing (then)
4  710810  936319

hope thats help :S sorry im a bit nubby on this thing !@@:mrgreen:

---

### Post by pay on 2006-12-30
Try```
sudo lspci | grep AGP
```and it should tell you what card you have

---


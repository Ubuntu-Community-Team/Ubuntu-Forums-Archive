---
title: "how do i get my hardware info?"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by ninjaprawn on 2007-10-20
im trying to find out wot type of memory my pc can use, things like max size, is it 2700, 333.....etc, i tried sudo lshw but it didnt give me much info on the memory!

any ideas?

thanks.

---

### Post by kaurman on 2007-10-20
The easiest and most accurate way is to look into your motherboard's user guide. If you know the model you can download it from the manufacturer's site.

---

### Post by ColombianGold on 2007-10-20
This shows some stuff

sudo lspci -v

if you want more...

sudo lspci -vvv

hope it helps..

CG

---

### Post by ninjaprawn on 2007-10-21
thanks

unfortunatly, my mainboard is ancient, and i cant find the manul online, just a basic version that doesnt tell me about the memory.

i tried;
sudo lspci -v
&
sudo lspci -vw

i couldnt get any info on the memory.

any more ideas?

thanks.

---


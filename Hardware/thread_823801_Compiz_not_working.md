---
title: "Compiz not working"
date: 2008-06-09
forum: Hardware
---

### Post by horuden on 2008-06-09
I have a HP 530 Laptop, with the Intel GMA 950 graphics drivers, and I cannot get desktop effects to work... I know my way around Linux, but am by no means a power user... can anyone think of some reason it wouldn't work??

---

### Post by nickdbliss on 2008-06-09
Give me the output of the following command
#lspci

And 

#glxinfo | grep rendering

---

### Post by stchman on 2008-06-09
> **horuden said:**
> I have a HP 530 Laptop, with the Intel GMA 950 graphics drivers, and I cannot get desktop effects to work... I know my way around Linux, but am by no means a power user... can anyone think of some reason it wouldn't work??

Compiz should work OOB with that card.  What version of Ubuntu are you using?  If you are using eariler than Gutsy Compiz was not very stable.

Boot the Hardy Live CD and Compiz should work.

---


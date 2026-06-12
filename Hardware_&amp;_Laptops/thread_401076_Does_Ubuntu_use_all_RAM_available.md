---
title: "Does Ubuntu use all RAM available ?"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by TomG on 2007-04-04
Hi, 

A french book called "Simple like Ubuntu" ([http://www.framabook.org/docs/SCU.pdf](http://www.framabook.org/docs/SCU.pdf)) mentions (translated) :
"**Please note that if you have a lot of RAM (1Gb or more) all your RAM will not be taken into account by the 386 kernel**".

1. Is that true ?
2. If yes why ?
3. How to get benefits of all the memory available (I have 2Gb) ?

Thanks :) 
TomG

---

### Post by teaker1s on 2007-04-04
It means ubuntu **can** use your ram if it needs to, it may be a memory limit of kernel

It doesn't mean ubuntu is resource hungry

---

### Post by ajgreeny on 2007-04-04
Some older kernels (I can't remember when it changed) will not detect more than a certain amount of ram, again I can't remember the figure, but don't worry, if you are using an up to date version of ubuntu, as I believe they all now can deal with this OK.  I think all your ram would still be useful instead of swap in any case.

---

### Post by az on 2007-04-04
> **TomG said:**
> 
"**Please note that if you have a lot of RAM (1Gb or more) all your RAM will not be taken into account by the 386 kernel**".

1. Is that true ?
2. If yes why ?
3. How to get benefits of all the memory available (I have 2Gb) ?


1. No.
2. Older versions of the 386 kernel had this issue.

Where (on what page) does it say that?  I looked, but could not find the statement.

---

### Post by TomG on 2007-04-04
Thanks guys for your answers :)
I've seen it on page 197 of the PDF document.

---

### Post by az on 2007-04-04
Ok, I found it.

Something else that is false is that the installer will chose the right kernel for you.  The desktop version will install the generic kernel since it will be the only one on the disk.  The generic kernel can enable features on-the-fly that used to be compile-time-only features in the past.

The other disks (PPC, 64-bit) only have their one respective kernel as well.

The author is misinformed.

---

### Post by faical117 on 2008-01-15
No just in old kernel .:lolflag:

---


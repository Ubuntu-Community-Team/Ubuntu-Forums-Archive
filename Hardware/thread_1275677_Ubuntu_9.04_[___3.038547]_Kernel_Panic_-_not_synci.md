---
title: "Ubuntu 9.04 [   3.038547] Kernel Panic - not syncing"
date: 2009-09-26
forum: Hardware
---

### Post by violettoulli on 2009-09-26
Hello all,

I am in India currently (wondering if my laptop is suffering from the heat???) and one day, suddenly when the previous day it had worked fine, I got this message when starting up (with Ubuntu 9.04):

[B]Boot from (hd0,3) ext3   ef7a9af7_1860_4357_9215_a64912090f9b
Starting up...
[   0.123689] ACPI: Aborted because broken padding.
[   3.025136] Invalid compressed format (err=1)
[   3.038547] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)[/B]

Then the machine stops and won't start. Now I had a similar problem before with Ubuntu 8.0 and as I am complete ignorant in terms of Linux, didn't do anything until I saw my friend 2 month later who reinstalled Ubuntu on my machine! Got 9.04 this time...

So I panicked a little, but when I start Ubuntu normally I get a list of versions of Ubuntu to chose from; 

Ubuntu 2.6.28-15 generic
Ubuntu 2.6.28-15 generic (recovery mode)
Ubuntu 2.6.28-14 generic
Ubuntu 2.6.28-14 generic (recovery mode)
Ubuntu 2.6.28-13 generic
Ubuntu 2.6.28-13 generic (recovery mode)

and actually, if I choose Ubuntu 2.6.28-14 generic (recovery mode) and Ubuntu 2.6.28-13 generic (recovery mode), after doing a bunch of 'things' that I don't understand AT ALL, filling the screen with gobbledigook, it gets to a menu where I choose "Repair broken packages"; the machine does that and then comes back to that menu, I choose "resume normal boot" (I forget exactly how it's called) and then it starts again, fine. 

So now, whenever I start up my computer, I have to start with the recovery mode (Ubuntu 2.6.28-**13** generic (recovery mode)) or Ubuntu 2.6.28-**14** generic (recovery mode)) cos Ubuntu 2.6.28-**15 **generic (recovery mode) won't work. And then it works totally fine (or at least it seems to me!)

How safe is it to always work with the recovery mode?
What the hell does this all mean?
What is a Kernel?

It's all Chinese to me...

Thank you for your help!!!
vio

---

### Post by koma77 on 2009-09-26
To me that sounds like the latest kernel is behaving badly. (When you select different intries in the boot menu you select different versions of the linux kernel).

Can you boot Ubuntu 2.6.28-13 generic? (_Not_ the recovery mode)

---

### Post by johny_ on 2009-10-05
Look if you can boot up the kernel mentioned by koma77 and let us know

---


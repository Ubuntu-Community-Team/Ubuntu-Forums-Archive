---
title: "New user, new install."
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by TheNeglected on 2009-05-27
Hello. I'm new here, so forgive me if I've posted this in the wrong section.

First of, I am new to Ubuntu. This is my first time installing it. 

Now, my problem.

When I start Ubuntu, and it loads, it gives me "Gave up waiting for root device", etc, 
along with ALERT! /dev/mapper/florence-root does not exist. Dropping to a shell, from 
then it loads to Initranfs. (florence is the computers hostname).

How can I attempt to fix this, and yes; I have added rootdelay=90 to the kernel, and it
doesnt fix it.

I have tried both 8 and 9, latest files, on the Server portion with nothing but the core installed. This is on a older system, IBM eSever xSeries with 2 processes. 

Thanks in advance!
Austin

---

### Post by orange-wedge on 2009-05-28
Are you using LVM for your partitions?

---

### Post by TheNeglected on 2009-05-28
Yes. I selected LVM.

---

### Post by abn91c on 2009-05-28
reboot wait about 5 seconds, type ```
exit
``` at the prompt post what happens

---

### Post by TheNeglected on 2009-05-28
Ubuntu loads as it should.

---

### Post by orange-wedge on 2009-05-28
Which version of Ubuntu are you using?  I remember having to load a module in the init script sometimes to get LVM partitions to be seen during boot.

---

### Post by TheNeglected on 2009-05-29
I honestly feel like a complete idiot. 
I first tried rootdelay=90 on a whole separate line, not with the kernel parameters, so i tried again, except actually added rootdelay=90 at the end of the kernel line, and it boots fine. no more problems! it must just take an extra moment for the hard drives to kick in. 

but, thanks again for the attempted help, and i hope somebody can learn from my silly mistake!

---


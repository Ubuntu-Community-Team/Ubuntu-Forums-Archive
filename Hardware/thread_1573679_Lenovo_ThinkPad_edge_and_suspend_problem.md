---
title: "Lenovo ThinkPad edge and suspend problem"
date: 2010-09-13
forum: Hardware
---

### Post by gstefan on 2010-09-13
Hi, 

I have Lenovo ThinkPad edge 14 with core-i5 processor and ATI graphics wiht Ubuntu 10.4:
2.6.32-25-generic-pae #43-Ubuntu SMP Wed Sep 1 11:17:51 UTC 2010 i686 GNU/Linux

Problem is repeatable, systems goes suspend only 2 succeeding times, third suspend leads always to system hang. 
I searched many discussions around that topic, but nothing helped. I have newest BIOS (3th of Sep). 
I also tested mainline kernel 2.3.35 and 2.3.36. Behavior is different:  in both cases suspend  stopped working at all (pm_suspend is ignored and nothing happened). I  can not see nothing in kern.log (no entries at all after issuing  command). 

Best regards

---

### Post by rCXer on 2010-09-13
Hi gstefan,

Others have reported the same problem ([here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/610093) and [here](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/573496)) but no solution has been found yet.

---

### Post by konni on 2010-09-23
hey gstefan,

i have a lenovo edge 13" and had a similar problem.
after second suspend everything stopped working, harddrives were mounted read-only, lots of errors in dmesg.

tried making my own dsdt file, didnt help anything. 
changing sata-mode from ahci to compability in bios did the trick then, maybe this helps ;)

---

### Post by sjonnie85 on 2010-11-09
> **konni said:**
> hey gstefan,

i have a lenovo edge 13" and had a similar problem.
after second suspend everything stopped working, harddrives were mounted read-only, lots of errors in dmesg.

tried making my own dsdt file, didnt help anything. 
[SIZE="5"]**_changing sata-mode from ahci to compability in bios did the trick then, maybe this helps_**[/SIZE] ;)

IT WORKED, THANK YOU!

But are you serious?? Why put the solution in the last sentence, I am sure it has been overlooked by many since your post gives the feeling that you failed to get it to work! :P

Anyway thanks again!

---


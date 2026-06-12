---
title: "Laptop locks up a few minutes after a resume from hibernate"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by grahams on 2007-06-18
Hi

I have an HP nw8440 running feisty. The laptop has an ATI x1600 graphics chip and this needs the ATI fglrx driver. Most things work great and my only real issue is with suspend/hibernate. Suspend does not work (at all) and the machine locks up a few minutes after resuming from hibernate. 

It looks like my system is slowly running out of resources after the resume as everything works fine for a while and then gets slower and slower and finally stops responding. I've run 'top' while this happens and I do not see anything hogging the CPU or any apparent memory leaks. Even after I can no longer access the system Top is still running and showing a healthy system. 

I'm guessing this is a problem with ATI's driver and X. 

Is anyone else running into this and if so know how to resolve?

---

### Post by Bluecircle on 2007-06-18
Try using my alternate suspend/hibernate fix here:

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by grahams on 2007-06-20
many thanks, I will give it a try and report back.

---

### Post by grahams on 2007-06-26
Running s2disk seemed to fix the hanging issue for a while, but it returned again.

---

### Post by chadjohnson on 2008-02-25
I have precisely the same problem. I also tried s2disk/s2both and had the same results.

---


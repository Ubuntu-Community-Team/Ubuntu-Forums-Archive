---
title: "kernel upgrade 2.6.25-26 causes slowdown"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by geos2 on 2006-07-19
On my ThinkPad x60s: when I upgraded to the 2.6.15-26 kernels I experience severe general slowdown in system performance.  This was evident with the 386 kernel but the 686-SMP kernel is essentially unusuable.  

Using the original 2.6.15-23 kernel fixes the problem, but the later kernels really improve support of this machine in other ways... 


Anyone?

---

### Post by Sef on 2006-07-21
What are your system specs?

---

### Post by didobuntu on 2006-07-21
strange, for me no difference between 2.6.15-23 and 2.6.15-25, and also with the last 2.6.15-26 ...

---

### Post by chadwick359 on 2006-07-22
I'm having a similar problem on my Pentium M laptop, though to me, it seems to be mostly an issue with the nVidia driver, because my apps themselves seem to be running well, just not when I try to move them. movies and amarok title/visulization are also affected, they have a noteable and constant acorss application stutter, but it is not nearly as bad as they were in -25

Edit:
I take that back, it just had to take a minute to get as bad as -25 was.

---

### Post by SishGupta on 2006-07-22
Nevermind. how can i delete this?

---

### Post by dlane on 2006-07-28
I also encountered major problems... symptoms:
 - high load average (apparently due to a failed hdparm of my CDROM drive launched by /etc/acpi/power.sh) 
 - slow application performance
 - boot problems related to "Load hardware drivers..." failing

No one else seems to cite the same boot problem in the forums...

Not sure what's wrong with the kernel - a switch back to 2.6.15-25-686 seems to return things to normal.

My platform:  Asus M3400N notebook (Pentium M), ipw2200 wireless...  with previous kernels, Sleep and Hibernate worked, but I haven't tested it recently...

Dave

---


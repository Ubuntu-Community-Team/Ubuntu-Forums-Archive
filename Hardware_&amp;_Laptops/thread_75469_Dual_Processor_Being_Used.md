---
title: "Dual Processor Being Used?"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by amerigo5 on 2005-10-13
I have 2 processors (AMD Athlon MP) on Tyan Thunder K7 motherboard.  How can I know if both are being used and how it is being used - percentage-wise?  The System Monitor only shows one graph (unlike Windows XP where it shows 2 graphs for each CPU).

Thanks.

---

### Post by Seth on 2005-10-13
Did you install the appropriate smp kernel?

---

### Post by Velox Letum on 2005-10-13
Yes, you must either compile or install a SMP (Symmetric Multi Processing) kernel in order to utilize multiple CPUs.

---

### Post by luckyaba on 2005-10-13
cat /proc/cpuinfo

should see in the output

processor 0
-
-
 processor 1

---

### Post by amerigo5 on 2005-10-13
cat /proc/cpuinfo shows that I am only using one CPU.

I am now installing the following packages:

-linux-image-2.6.12-9-k7-smp
-linux-image-k7-smp
-linux-restricted-modules-2.6.12-k7-smp
-linux-restricted-modules-k7-smp

Comments please....

Thanks!!!

---

### Post by amerigo5 on 2005-10-13
Everything works perfectly now.  Thanks everyone for the help!!!

---

### Post by MySchizoBuddy on 2005-10-21
did u compile it or installed deb files
and how did u configure it

---


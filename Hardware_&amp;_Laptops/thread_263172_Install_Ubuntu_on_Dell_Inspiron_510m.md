---
title: "Install Ubuntu on Dell Inspiron 510m"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by vinodmenon on 2006-09-22
Hi All,
  I have a Dell Inspiron 510m laptop and would like to install the latest "Dapper Drake" version of Linux along with my windows running together. My current specs for the laptop are as follows:

Features/Specs: Pentium M 1.6GHz; 512MB RAM; 15in screen; 64MB shared Intel Extreme Graphics 2; 60GB hard drive; DVD-RW/CD-RW

Is there any way anyone could assist me with the installation procedures for having a dual-boot system on this laptop? Any guides or website? I believe that i have to recreate the partitions in order to have the dual-boot work properly. Currently my laptop has been reset to factory conditions ie like brand new when i got it delivered with Windows OS etc. I have just installed Partition Magic after ghosting the hard disk.

Hoping to resolve this matter asap.
-- 
Regards,
Vinod Menon

---

### Post by Sef on 2006-09-22
> Is there any way anyone could assist me with the installation procedures for having a dual-boot system on this laptop? Any guides or website? I believe that i have to recreate the partitions in order to have the dual-boot work properly.

To Dual Boot, [click here.]("http://users.bigpond.net.au/hermanzone/")

> have just installed Partition Magic after ghosting the hard disk.


It is best **NOT** to use Partition Magic.  It and GNU/Linux often do not get along.  Use the partitioner on the Live Install/alternate CD.

---

### Post by vinodmenon on 2006-09-22
Ok! That's fine but what about QParted Partition Software? Would that work? The reason being i already have dell utility occupying a certion portion of the hdd on my laptop.

---

### Post by vinodmenon on 2006-09-23
Anybody managed to isntall Dapper Drake successfully? Partioning the harddsik, any troubles\problems encountered? Any help would be most appreciated! Thanks!

---

### Post by vinodmenon on 2006-09-27
Ah Yes, I do believe i have fixed this problem, all i had to do was to resize the existing partition with destroying anything else, my DELL UTILITY partition and CTOS, DOS is still there. Managed to dual boot WinXP and Ubuntu. GRUB allows me to choose which OS to run. I also had no problem with sound cards, network cards, battery and USB devices. This is simply fantastic!

Now i can't wait to do more with my Ubuntu, get XGL Compiz to work on it. Dapper Drake 6.06 rulez!

---


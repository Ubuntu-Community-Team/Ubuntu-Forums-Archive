---
title: "Problem with AMILO Pro V3535 laptops"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by pOPaji on 2007-10-02
I work as IT administrator in a school, got some AMILO Pro V3535 laptops but ubuntu isnt working properly in general it works so slow and also wireless doesnt work. I also got a bizhub 250 printer and cant find a driver for these laptops:confused:

---

### Post by heidfirst on 2007-10-03
I run ubuntu 6.10 on an Amilo Pro V3505 and have to admit it works very well.  Wireless was a bit of a problem to start with but found a solution from a fedora user.

If it is a case of ubuntu does not enable the wireless chip set from cold boot then you could try the following as root.  

The V3505 has the Intel PRO/Wireless 3945ABG

> 
modprobe acerhk
echo 1 > /proc/driver/acerhk/wirelessled


I have this as script that I can run when I need wireless switched on.

Can't help with the printer.

Gordon

---


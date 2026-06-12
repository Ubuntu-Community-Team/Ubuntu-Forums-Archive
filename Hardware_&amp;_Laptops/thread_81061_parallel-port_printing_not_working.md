---
title: "parallel-port printing not working"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by esj on 2005-10-23
I am running ubuntu 5.10 as a server and I was astounded when I could not print over the line printer port.  Two different printers, two different cables both failed.  It's a brand new Intel motherboard (945GNT)  with more options then you can shake a stick at on the parallel port.   when I look at the output of dmesg, I can see that the kernel has recognized the physical hardware and assigned it to lp0.

I try my laptop running 5.10 on a different printer in my office and it works fine.  Obviously I'm going to try this laptop at the customer site.

now as far as I can remember, parallel-port printers just work.  It's one of the few things you can count on to function.   So I am a little curious as to why something so ordinary should cause a problem now?

---

### Post by chrisTGc on 2005-12-20
Useing;
$ sudo modprobe parport_pc
System>Administration>Printing>add printer
solved similair problems foe me,best wishes Chris.

---


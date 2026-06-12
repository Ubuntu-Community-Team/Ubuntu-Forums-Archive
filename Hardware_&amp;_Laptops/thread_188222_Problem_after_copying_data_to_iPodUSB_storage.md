---
title: "Problem after copying data to iPod/USB storage"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by billybofh on 2006-06-03
After upgrading to dapper I've seen some odd USB problems.  Initially I couldn't access any of my USB mass-storage at all, then found a thread where someone suggested removing the ehci_hcd module - which magically let all of the USB devices appear and be mounted.

How-ever, if I copy data to them (for instance on the iPod either as USB storage or using gtkpod etc) then when I try to umount or sync it will sit forever (or at least I let it overnight and it hadn't finished....).

Nothing appears in dmesg or /var/log/* to indicate a problem.

A certain amount of the data does seem to be copied ok - but not all of it.

System is : 2.6.15-23-amd64-generic #1 SMP PREEMPT.  nForce chipset.

Anyone else seen this?

---


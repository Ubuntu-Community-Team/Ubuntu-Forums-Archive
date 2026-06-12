---
title: "Integrated ethernet fails on Inspiron 8100"
date: 2008-07-18
forum: Hardware
---

### Post by kayinart on 2008-07-18
I installed 8.04 about 2 hours ago and have been struggling to get the integrated ethernet card to work since.  When I run ifconfig only the loopback is listed.  When I run lspci the ethernet card is listed as-

08:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)

I searched for the past 30 minutes and could not find a solution.  Please help!

---

### Post by kayinart on 2008-07-23
Can somebody help me?  It's been 4 days and I still haven't been able to fix it :S

---

### Post by asamax01 on 2008-11-16
Same problem, different versions:
xubuntu 8.10

banano@NB1:~$ lspci | grep -i ethernet
returns:
08:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)

banano@NB1:~$ uname -a
returns:
Linux NB1 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

is my card running?
is a proper module installed?
no ethernet = no internet = very big trouble

please help US
thx in advance - m.

---


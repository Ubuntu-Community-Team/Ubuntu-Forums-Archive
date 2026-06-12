---
title: "Ubuntu 8.04 &amp; 8.10 lock up SATA"
date: 2008-11-11
forum: General Help
---

### Post by mrjerryk on 2008-11-11
Hello,

Currently I have 8.04.1 installed.  My system locks up about half the time I try and access either of my two 500GB SATA drives.  There are no log files generated for this lockup either.  The system just stops responding.  Can someone please tell me what I need to do in order to fix this problem.

I have also tried to install 8.10 Intrepid Ibex and I get the same results.  Like I said this only happens about half the time and not every time I try to access these drives and the lock ups only occur when I or another application is trying to access these drives.  These are also mounted under /media/mount name.



Specs.

Processor	AMD Athlon(tm) 64 Processor 3200+
Memory	        3GB
Video Card	GeForce 7600 GS/AGP/SSE2/3DNOW!
Motherboard     Giga-byte K8U-939
HDD 1           Wester Digital 80GB IDE
HDD 2           Seagate 500GB SATA
HDD 3           Hitachi 500GB SATA



Thanks in advance for your help.

---

### Post by mrjerryk on 2008-11-11
bump

---

### Post by Green_Star on 2008-11-11
I too have same problem, I have one SATA disk, it wasn't worked file in 7.10 and some how worked okey in 804(used to freeze rarely) not it is again stated freezing when ever I access.

I tried upgrading to 810 but still no luck. As OP mentioned ubuntu is not writing any logs, it just hangs, I had to do hard reboot.

---

### Post by mrjerryk on 2008-11-12
bump again. I really don't want to have to go back to winblows.  When I left I tried to leave for good.  Even formatted  my 2 500GB drives and made them ext3.

nobody has any ideas what I could try here?

---

### Post by mcg on 2009-01-03
What SATA controller and drives do you have?  I'm having a similar issue.

---

### Post by mrjerryk on 2009-01-03
I found out that my problem was actually my onboard SATA controller.  It completly went out about 2 weeks after my post.  I just went out and bought a PCI SATA controller from microcenter and it works great.  Linux picked it up without a hitch.

I also boot from this card as well.

---


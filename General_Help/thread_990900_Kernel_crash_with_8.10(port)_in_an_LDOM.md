---
title: "Kernel crash with 8.10(port) in an LDOM"
date: 2008-11-23
forum: General Help
---

### Post by davidmarkey on 2008-11-23
using the netboot image from [http://ports.ubuntu.com/ubuntu-ports/dists/intrepid/main/installer-sparc/current/images/netboot/](http://ports.ubuntu.com/ubuntu-ports/dists/intrepid/main/installer-sparc/current/images/netboot/)

I get a kernel crash when trying to install into a T1000 LDOM:


[   76.842282] SUN4V-DTLB: Error at TPC[f7d4baac], tl 1
[   76.842282] SUN4V-DTLB: Error at TPC[f7d4baac], tl 1
[   76.844850] SUN4V-DTLB: TPC<0xf7d4bab4>
[   76.844850] SUN4V-DTLB: TPC<0xf7d4bab4>
[   76.847393] SUN4V-DTLB: O7[f7eb9a88]
[   76.847393] SUN4V-DTLB: O7[f7eb9a88]
[   76.848821] SUN4V-DTLB: O7<0xf7eb9a90>
[   76.848821] SUN4V-DTLB: O7<0xf7eb9a90>
[   76.852821] SUN4V-DTLB: vaddr[f7c58000] ctx[1c0] pte[98000000000f0610] error[2]
[   76.852821] SUN4V-DTLB: vaddr[f7c58000] ctx[1c0] pte[98000000000f0610] error[
2]
                  


And the system freezes. The installer got to when is was downloading the base packages from ports.ubuntu.com


To date 7.10 is the only release i can get to run in an LDOM with any stability.


can the team that maintains this port please look into the issue?


thanks.

---

### Post by Sef on 2008-11-23
> To date 7.10 is the only release i can get to run in an LDOM with any stability.


can the team that maintains this port please look into the issue?Ubuntu does not support Sparc any more except for Dapper Drake, 6.06.  Desktop updating expire June 2009, and server updating expire June 2011.

---

### Post by Sef on 2008-11-23
> To date 7.10 is the only release i can get to run in an LDOM with any stability.


can the team that maintains this port please look into the issue?

Ubuntu does not support Sparc any more except for Dapper Drake, 6.06.  Desktop updating expires June 2009, and server updating expires June 2011.

---

### Post by davidmarkey on 2008-11-23
> **Sef said:**
> Ubuntu does not support Sparc any more except for Dapper Drake, 6.06.  Desktop updating expire June 2009, and server updating expire June 2011.


I know that but someone in the community must be maintaining the port that i specified([http://ports.ubuntu.com/dists/intrepid/main/installer-sparc](http://ports.ubuntu.com/dists/intrepid/main/installer-sparc)). So i would appreciate if you can bring it to their attention even though it it not supported.


Give me their contact details and i will chase it up myself.

Thanks

---

### Post by 60hbe16es52 on 2009-01-12
is [aoc power leveling](http://www.aoc-power-leveling.org) and [age of conan power leveling](http://www.aoc-power-leveling.org) the same mean??

---


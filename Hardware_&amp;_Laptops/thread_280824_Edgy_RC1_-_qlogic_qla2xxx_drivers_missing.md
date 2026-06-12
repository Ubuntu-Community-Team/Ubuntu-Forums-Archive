---
title: "Edgy RC1 - qlogic qla2xxx drivers missing?"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by redhatsoff on 2006-10-20
Hi all,

Have been using a qlogic HBA card with Dapper without too many problems. Just tried out the edgy release candidate and noticed that the qla2xxx drivers seem to missing. Doing a search on packages.ubuntu.com shows the files in the 2.6.15 kernel, but not the 2.5.17 kernel that comes with edgy RC1. Has anyone got a qlogic card working under edgy or know why these drivers have apparently been removed? :-k 

Cheers,
Tom

---

### Post by nivex on 2006-10-21
A friend of mine just encountered that problem as well.  He has filed a bug against the kernel package in the hopes of getting it resolved in time for release:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67463](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67463)

-- Kevin

---

### Post by redhatsoff on 2006-10-22
Cheers for the reply. Let's hope they get it resolved before release.

---

### Post by elicriffield on 2006-10-23
I just upgraded to edgy from dapper on a IBM Blade Center with qlogic QLA2312 cards san booting and the new 2.6.17 kernel has no driver.

I remember something about the qlogic drivers firmware being removed from the kernel modules and is now loaded from a separate file outside the modules directory when the 2.6.16 kernel came out. Maybe thats why we don't have drivers now?

Eli

---


---
title: "Athlon 64 3500+ and Ubuntu speed"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-03-02
Hello all.  I installed Ubuntu on my Athlon 64 3500+ machine.  The only thing is that Ubuntu reports the processor as running at 1GHz.  The 3500+ runs at 2.2GHz.  Does anyone know why this is happening?  I know that Athlon 64 processors can have their clock stepped down with the proper drivers.  Does Ubuntu use this speed controlling technology?

Thanks

---

### Post by capitalistpiglet on 2007-03-02
Is this a laptop or desktop machine? My laptops amd turion steps down its clock speed to help conserve power when not under a heavy load. If its a desktop it may be that ubuntu just isnt reading the speed correctly.

---

### Post by stchman on 2007-03-02
> **capitalistpiglet said:**
> Is this a laptop or desktop machine? My laptops amd turion steps down its clock speed to help conserve power when not under a heavy load. If its a desktop it may be that ubuntu just isnt reading the speed correctly.

It is a desktop machine.

---

### Post by stchman on 2007-03-02
I was doing a little more reading and it seems that Ubuntu installs Cool 'n' Quiet drivers by default on AMD procs that utilize this technology.  This causes the proc to throttle down to a lower clock speed when under light loads.

---


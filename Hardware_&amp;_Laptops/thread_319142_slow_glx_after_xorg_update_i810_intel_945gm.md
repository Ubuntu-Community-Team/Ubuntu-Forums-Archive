---
title: "slow glx after xorg update i810 intel 945gm"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by suoko on 2006-12-15
Hi,

I'm now experiencing very slow 3d acceleration after xorg update with my intel 945gm card.

What's up ??

---

### Post by charles.figura on 2006-12-15
I've seen this too.  I've got a Dell D620 with the 945gm chipset, and I had been getting ~1800fps on glxgears under Dapper.  When I updated to Edgy, I'm only getting ~1000fps.  It's certainly still usable, but a little disconcerting.  Anyone else see this?  Any ideas?  Suoko, did you do a dist-upgrade, or is this an upgrade within Edgy?

---

### Post by jadahl on 2006-12-18
When upgrading from ubuntu to edgy my intel graphics GLX stopped working completly. Though when disabling dual head it atleast didn't crash, now it just doesn't work (getting the error libGL warning: 3D driver claims to not support visual 0x5b).

---

### Post by suoko on 2006-12-19
I did an edgy clean install. However 3d used to work until recent upgrade of xorg packages.

---


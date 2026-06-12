---
title: "Upgrade from 7.1  to 8.04 except Evolution"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by ant0ny on 2009-01-19
Hi,

I installed 8.04 but shortly found out that Evolution Mail 2.22 has a magor problem using exchange server.

I then installed 7.1 and Evolution 2.1 works great.

How can I do a *apt-get install dist-upgrade *and exclude Evolution from being upgraded?

I have actually setup 2 machines one with 7.1 and one with 8.04... So if the solution is easier to downgrade Evoltion on 8.04 back to 2.1 this would also be just as good or even better for me.

Antony

---

### Post by cariboo on 2009-01-20
You can pin Evolution at the version you want by going to System-->Administration-->Synaptic Package Manager-->Package-->Lock Version. Make sure you have highlighted Evolution first.

Jim

---

### Post by ant0ny on 2009-01-20
> **cariboo907 said:**
> You can pin Evolution at the version you want by going to System-->Administration-->Synaptic Package Manager-->Package-->Lock Version. Make sure you have highlighted Evolution first.

Jim

Yes thanks Jim but that was the first thing I tried. 

When you open the **Update Manager **it says **Partial Update **which sounds encouraging but if you scroll down the list of packages that will be upgraded you will see **Ugrade Evolution** is there.

Thats why I thought trying to use an exclusion with apt-get might be the way to go.

Antony

---


---
title: "Automatic updates questions"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by melopsittacus on 2009-03-27
Hello!

There is a package (VirtualBox 2.1) which I do not want being automatically updated. Is there a way of permanently ignoring updates for certain packages?

The other question is: does auto updates handle the situation when download of new packages is interrupted and restarted? I did so, because I had actually forgotten disable update for Virtualbox.
The installation console did not give any errors, however I would like to verify it (in order not to accidentally miss any security updates...) For this I would need two commands:
- one that lists the packages that were updated when auto-update was run last time
- one that checks integrity for a given installed package (and wether it is really at its newest version)

Thanks,


melopsittacus

---

### Post by albandy on 2009-03-27
go to synaptic, search for the package and block it

---

### Post by melopsittacus on 2009-04-07
> **albandy said:**
> go to synaptic, search for the package and block it

What does "blocking" mean? I could not find it anywhere...

---

### Post by Partyboi2 on 2009-04-07
You can prevent a package from being upgraded by opening up synaptic and searching the for the package you don't want upgraded, then highlight it and select Package>Lock Version, this should then prevent the package from being upgraded.

---

### Post by melopsittacus on 2009-04-11
Thank you, I did not know about this useful feature :)

---


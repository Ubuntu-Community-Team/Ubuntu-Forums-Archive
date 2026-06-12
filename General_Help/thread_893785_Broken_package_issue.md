---
title: "Broken package issue"
date: 2008-08-18
forum: General Help
---

### Post by master.swarky on 2008-08-18
Hello guys, need your help :)

I'm running Xubuntu 8.04 and I have actually ran into a problem with my package manager.

The matter is that I needed to install a package of a version, superior to one in hardy repositories. Luckily, the needed package was found in Debian repo. So, I removed the hardy package, downloaded the debian one and installed it via 'dpkg -i' command.

It worked perfectly, the new package is working just perfectly, but now my package manager keeps telling me that this package is broken and needs reinstalling (i.e. downgrading to hardy one, I presume).

So, the question is: how can I tell my package manager to omit this package while looking for broken packages?

Thanks in advance,

// Cheers :)

---

### Post by x1a4 on 2008-08-18
If you're using aptitude you can use the **forbid-version** action.  For example: 
```

sudo aptitude forbid-version *package*=*version*

```
*version* has to be the full version and build.

Neither Synaptic nor apt-get have this functionality.

---

### Post by master.swarky on 2008-08-18
Ummm.. Should I put the version of the hardy package or the debian one?

---


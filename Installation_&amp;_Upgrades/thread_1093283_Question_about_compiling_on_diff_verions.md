---
title: "Question about compiling on diff verions"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by sippyCUP on 2009-03-11
Hi all,

I recently upgraded from Ubuntu 8.04 to 8.10, but now that I've bought a new HDD I'm reverting to 8.04 because I've discovered that I don't appreciate the improvements in 8.10 but definitely have taken heed of a few problems (mostly the networkmanager).

My question: If I've compiled programs on 8.10, will I be able to move to my 8.04 install them by simply cp'ing the files and resetting the appropriate environmental variables and/or path? Or since 8.04 uses a different version of gcc, etc, will it not work?

I'm sort of confused about this because although both installs are on the same hardware, I'm not sure what the determining factor is for determining if Binary A, compiled say for Redhat, will work on Ubuntu, or vice-versa. A lot of vendors provide binaries, but they are only "guaranteed" to work on a certain distro and version. So by extension I don't know if something compiled under 8.10 will necessarily work on 8.04.

Thanks for your time,
Eric

---

### Post by taurus on 2009-03-11
As long as you have the necessary libraries for it, it should run.  To check, run this command from a terminal, assuming you are in the same directory where the binary is.

```
ldd app_name
```

---


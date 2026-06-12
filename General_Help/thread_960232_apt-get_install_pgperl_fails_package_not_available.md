---
title: "apt-get install pgperl fails: package not available"
date: 2008-10-27
forum: General Help
---

### Post by brunogirin on 2008-10-27
I've been trying to install pgperl on Ubuntu Hardy and when I try to do this, I get the following error message:

```
bruno@nuuk:~$ sudo apt-get install pgperl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pgperl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package pgperl has no installation candidate

```

I currently have main, universe, restricted, multiverse and source code enabled as software sources in sources.list so it doesn't look like I am missing any of them.

Does anyone know how I can get pgperl? Does it come as part of another package?

Thanks in advance for any help!

---

### Post by geirha on 2008-10-27
```
aptitude search pg.*perl
```

Could libpg-perl be the package you're looking for?

---


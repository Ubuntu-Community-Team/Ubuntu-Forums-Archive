---
title: "Could not initialize the package information error (Ubuntu 9.04)"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by dusanlazic7 on 2009-06-09
An unresolvable problem occured while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '[quote]' is not know on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be red.'

This is the error message I get when i try to to run Update Manager. Any help please?

---

### Post by Partyboi2 on 2009-06-10
Hi, looks like there could be a problem with an entry in your sources.list. Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

---


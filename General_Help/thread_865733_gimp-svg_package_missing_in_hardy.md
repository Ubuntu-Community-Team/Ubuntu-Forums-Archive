---
title: "gimp-svg package missing in hardy"
date: 2008-07-20
forum: General Help
---

### Post by rhussong on 2008-07-20
The gimp-svg plugin is apparently unavailable in Hardy, and I haven't been able to find a compatible version elsewhere.  Does anyone know why the package is missing, and if there is a version of the plugin that works in Hardy?

---

### Post by ranch hand on 2008-10-27
This is all I could find out easily.  I would assume ou don't need it.

I think gimp is great.


tom@hogwash:~$ sudo apt-get install gimp-svg
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gimp-svg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gimp
E: Package gimp-svg has no installation candidate

---

### Post by dariusdwtt on 2008-12-07
bump

---

### Post by Unterseeboot_234 on 2008-12-08
Same thing in Ubuntu 8.10, no Save, Save As or any export for .svg -- Gimp 2.6.1. Dapper was the last version Ubuntu with the GIMP to accomplish .svg graphics (that I can remember). I don't know if this is a Launchpad issue or if I was supposed to build my own Gimp.

But, Debian Etch has Gimp with SVG capabilities.

---

### Post by Unterseeboot_234 on 2008-12-09
Gimp has moved .SVG as a Path Export script listed in available plug-ins.

1. in the Help files for Gimp, they list .SVG format as Open / Save

2. But, over in the Gimp features / download site, they do not list .SVG and suggest many plug-ins offer additional file capabilities. I found an SVG Export, however it is a Script, not a plug-in. In the description for the SVG Export plug-in it says "provided SVG support has been factored in during the build [of Gimp]". It has. Gimp Ubuntu will open .SVG files as a bitmap representation. If you create paths or trace THEN you can use a Script to get those paths.

**[Gimp SVG script]("http://registry.gimp.org/node/100")**

---


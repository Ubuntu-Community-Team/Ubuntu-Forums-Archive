---
title: "Installing RMP packages natively in Ubuntu."
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-06-04
i.e by bypassing the debian packaging system.

Ok, I downloaded that RMP package from the repos...I tried to install an RMP package (command line; rmp -i <package>.rpm).

It ended up with a dependency problem but those packages are already installed in the Debian packaging system :confused:


Any solutions?

---

### Post by Mark Phelps on 2009-06-04
Try using alien to convert the package to .deb and see it that works.

---

### Post by cariboo on 2009-06-04
Most rpm based distributions are set up slightly different from deb systems. Some of he file locations are different. If the package is available as a deb I would use that instead, as the dependencies are taken care of.

---

### Post by dE_logics on 2009-06-04
I'm trying to natively install that, i.e no package convention, Or I'm trying to make the Debian distribution an RPM based.


Anyway to redefine the paths for that rpm command?...I think that's causing the issue...it said some folders were not found.

---


---
title: "problems with update manager"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by maboli on 2009-05-13
after i finished the installation of ubuntu 9.04 my update manager gives me this massage 

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'  "


what should i do

---

### Post by Brandon Williams on 2009-05-13
It sounds like your package cache got corrupted somehow. Most likely, the problem will go away if you update the package cache. Try running 'sudo aptitude update' on the command line. If that doesn't resolve the problem, let us know and we will help you take more drastic action.

---

### Post by maboli on 2009-05-16
thank you ... problem solved

---


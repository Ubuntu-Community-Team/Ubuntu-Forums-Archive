---
title: "Can't Install Funguloids"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by vonsperb on 2009-01-04
I can't install Funguloids. The Add/Remove... application ask me to use Synaptics, but Synaptics complains about:

funguloids:
 Depends: ogre-plugins-cgprogrammanager  but it is not installable

If I try to install it with apt-get:

laptop:~$ sudo apt-get install ogre-plugins-cgprogrammanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ogre-plugins-cgprogrammanager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ogre-plugins-cgprogrammanager has no installation candidate

---

### Post by Partyboi2 on 2009-01-05
ogre-plugins-cgprogrammanager is not currently in the ubuntu repositories. You can read the bug report  [URL="https://bugs.launchpad.net/ubuntu/+source/funguloids/+bug/194686"][COLOR=Blue]here[/COLOR].
[/URL]

---

### Post by vonsperb on 2009-01-05
OK, thanks!

---


---
title: "Installing nvidia Drivers on amd64"
date: 2005-11-25
forum: General Help
---

### Post by rebo on 2005-11-25
Cant seem to install the latest nvidia drivers, any ideas ? Here is the error from my log file , any ideas?

-> Running runtime sanity check:
ERROR: The runtime configuration check failed for library 'libGL.so.1.0.7676'
       (expected: '/emul/ia32-linux/usr/lib/libGL.so.1', found: 'not').  The
       most likely reason for this is that conflicting OpenGL libraries are
       installed in a location not inspected by `nvidia-installer`.  Please be
       sure you have uninstalled any third-party OpenGL and third-party
       graphics driver packages.
-> done.
-> Runtime sanity check failed.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by cdhotfire on 2005-11-26
[quote=rebo]Cant seem to install the latest nvidia drivers, any ideas ? Here is the error from my log file , any ideas?

-> Running runtime sanity check:
ERROR: The runtime configuration check failed for library 'libGL.so.1.0.7676'
       (expected: '/emul/ia32-linux/usr/lib/libGL.so.1', found: 'not').  The
       most likely reason for this is that conflicting OpenGL libraries are
       installed in a location not inspected by `nvidia-installer`.  Please be
       sure you have uninstalled any third-party OpenGL and third-party
       graphics driver packages.
-> done.
-> Runtime sanity check failed.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com").[/quote]

Did you uninstall nvidia-glx?

---

### Post by rebo on 2005-11-26
Yes I uninstalled nvidia-glx

---

### Post by metoo on 2005-11-26
Did you follow the right procedure? I don't have any /emul/... directory on my breezy64.

You are installing the original from nvidia?

You might have your reasons, but just to point out that 7667 comes already as a pre-compiled package for your kernel in breezy.
Search in synaptic for it, you might have to extend your source lines in /etc/apt/source.list with restricted or universe or multiverse .

---


---
title: "Looking Glass Installation trouble"
date: 2008-08-13
forum: General Help
---

### Post by pikabuntu on 2008-08-13
I get this when I try to install the looking glass desktop environment
does this mean that xorg is missing? if so, what can I do?
(I hope that this was the right section to post in :))

zach@zach-desktop:~$ sudo apt-get install lg3d-core
[sudo] password for zach: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lg3d-core is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++5 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
zach@zach-desktop:~$

---


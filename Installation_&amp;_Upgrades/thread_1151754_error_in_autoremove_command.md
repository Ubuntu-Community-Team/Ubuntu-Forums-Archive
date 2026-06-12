---
title: "error in autoremove command"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by mosaic2s on 2009-05-07
linux@chota-rajan:~$ apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  virtualbox-ose-source nvidia-180-libvdpau
The following packages will be REMOVED:
  nvidia-180-libvdpau virtualbox-ose-source
0 upgraded, 0 newly installed, 2 to remove and 12 not upgraded.
After this operation, 5673kB disk space will be freed.
Do you want to continue [Y/n]? y
**Segmentation fault**
linux@chota-rajan:~$ 

Any suggestions where I went wrong?

---


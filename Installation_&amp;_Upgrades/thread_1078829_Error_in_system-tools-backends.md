---
title: "Error in system-tools-backends"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by phaed on 2009-02-23
Has anybody else been getting an error in the last few days whenever they update/upgrade?  I keep getting this error about system-tools-backends:

```
The following partially installed packages will be configured:
  system-tools-backends 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                                                                                       
invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Partyboi2 on 2009-02-23
Try removing the package then reinstalling it.
```
sudo apt-get remove system-tools-backends 
```This will probably remove fast-user-switch-applet, gnome-applets, gnome-system-tools and liboobs-1-4 but you can reinstall those after you have reinstalled system-tools-backends.
```
sudo apt-get install system-tools-backends
```then
```
sudo apt-get install fast-user-switch-applet gnome-applets gnome-system-tools liboobs-1-4 ubuntu-desktop

```

---

### Post by phaed on 2009-02-23
When I tried removing it before it said it was going to remove ubuntu-desktop, so I canceled it.  But I did what you said and it worked.  Thanks.

---

### Post by michael4096 on 2009-02-25
Warning - for me this only works with apt-get as described. Synaptic introduces the same problem again

Also - while the problem exists some apps do funny things. On mine, Firefox wouldn't display the screen properly

---


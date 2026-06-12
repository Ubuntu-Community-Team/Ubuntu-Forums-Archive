---
title: "[SOLVED] Unable to start Synaptic"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by ancient_ee on 2008-12-27
In trying to upgrade VirtualBox to V2.10, I added [http://dlc.sun.com/virtualbox/vboxdownload.html](http://dlc.sun.com/virtualbox/vboxdownload.html) to my Synaptic source list. Now Synaptic will not start. The error message is:

An error occurred.
The following details are provided:

E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I am sure there is a text file somewhere that must be edited. Please point me to it.

---

### Post by taurus on 2008-12-27
You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove that line that you added in, line 56.  Then, save it and close down gedit editing window.  Now run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ancient_ee on 2008-12-27
Thanks!

---


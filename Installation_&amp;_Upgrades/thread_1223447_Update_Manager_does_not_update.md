---
title: "Update Manager does not update"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by netjohnston on 2009-07-26
Hi,

my system is dual boot: Windows XP and Ubuntu 9.04.  The Update Manager 
cannot update after installation and the error message I got is


    Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


Please, can someone help?

netjohnston

---

### Post by spd106 on 2009-07-26
First try opening the System -> Administration -> Software Sources program and change the Download from server to one in your locale using the other option then select the best server (e.g. I use "Server for United Kingdom").  

Save and reload the repository information.

If that doesn't fix the error can you please post the contents of your /etc/apt/sources.list file?

---

### Post by Soul-Sing on 2009-07-26
```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by netjohnston on 2009-07-26
> **spd106 said:**
> First try opening the System -> Administration -> Software Sources program and change the Download from server to one in your locale using the other option then select the best server (e.g. I use "Server for United Kingdom").  

Save and reload the repository information.

If that doesn't fix the error can you please post the contents of your /etc/apt/sources.list file?
Problem solved.
Thanks.

netjohnston

---


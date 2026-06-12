---
title: "help with synaptic package manager"
date: 2008-08-07
forum: General Help
---

### Post by env2156 on 2008-08-07
ok i was trying to download limewire which has a debian package for install, it was installing and it froze mid way through the process and i had to restart my comp. so now when i try to install its telling me i neeed to close another synaptic or something like that but there is no other one running at all. and when i try to go to synaptic package manager its throwing this error message " E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. "  can somone please help me with this i need to get this fixed soon as possible and im still newish

---

### Post by Vivaldi Gloria on 2008-08-07
Try running

```
sudo dpkg --configure -a
```

in a terminal.

---

### Post by GreenN00b on 2008-08-07
Open a terminal and try to run
```
sudo dpkg --configure -a
```

---

### Post by env2156 on 2008-08-07
dpkg: dependency problems prevent configuration of sun-java6-bin:
sun-java6-bin depends on sun-java6-jre (= 6-06-0ubuntu1); however:
Package sun-java6-jre is not installed.
dpkg: error processing sun-java6-bin (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
sun-java6-bin

i have that, how do i repair whatever is broken

---

### Post by plucky on 2008-08-07
> **env2156 said:**
> dpkg: dependency problems prevent configuration of sun-java6-bin:
sun-java6-bin depends on sun-java6-jre (= 6-06-0ubuntu1); however:
Package sun-java6-jre is not installed.
dpkg: error processing sun-java6-bin (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
sun-java6-bin

i have that, how do i repair whatever is broken

Either **System > Administration > Synaptic Package Manager > Status** and find and fix broken package.

Or open a terminal and ```
sudo apt-get install -f
``` and it should try to fix your "sun java" install.Remember that you need to accept the Sun EULA before these programs will install, so you need to respond when it asks you.


Good Luck

---


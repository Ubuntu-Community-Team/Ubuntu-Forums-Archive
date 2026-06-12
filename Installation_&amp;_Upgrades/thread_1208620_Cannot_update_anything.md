---
title: "Cannot update anything"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by Tyrfing on 2009-07-09
Hello, I am currently running Ubuntu 8.04, and I cannot upgrade any program. Whenever I try to run an update, I always get this error message:


E: python2.5-minimal : subprocess post-installation script returned error exit status 1

Does anyone have any ideas on what to do? Or what other information I can retrieve to help diagnose this problem? Thanks so much!

 -Tyrfing

---

### Post by Tyrfing on 2009-07-09
bump

---

### Post by Tyrfing on 2009-07-09
bump2

---

### Post by Tyrfing on 2009-07-10
bump3...

---

### Post by geekity2 on 2009-07-10
Hi Tyrfing,

did you run the upgrade through the gui or using apt/aptitude? If you run ```
sudo aptitude update && sudo aptitude safe-upgrade
``` it may give you some options to fix this...

---

### Post by Tyrfing on 2009-07-10
I tried that command, this was the result...











Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up python2.5-minimal (2.5.2-2ubuntu4.1) ...
Linking and byte-compiling packages for runtime python2.5...
pycentral: pycentral rtinstall: package python-imaging: not overwriting local files
pycentral rtinstall: package python-imaging: not overwriting local files
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python2.5-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.5-minimal (2.5.2-2ubuntu4.1) ...
Linking and byte-compiling packages for runtime python2.5...
pycentral: pycentral rtinstall: package python-imaging: not overwriting local files
pycentral rtinstall: package python-imaging: not overwriting local files
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.5:
 python2.5 depends on python2.5-minimal (= 2.5.2-2ubuntu4.1); however:
  Package python2.5-minimal is not configured yet.
dpkg: error processing python2.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.5-dev:
 python2.5-dev depends on python2.5 (= 2.5.2-2ubuntu4.1); however:
  Package python2.5 is not configured yet.
dpkg: error processing python2.5-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.5-minimal
 python2.5
 python2.5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done

---

### Post by jrox717 on 2009-07-10
It seems like the problem has to do with the package python2.5 and related packages. I'm not sure if this is what you need to do, but I would try to remove it.
```
 sudo apt-get purge python2.5 
```
(Purge deletes all config files in addition to the package itself.) If needed, also manually get rid of python2.5-minimal or python2.6-dev

---

### Post by Soul-Sing on 2009-07-10
```
sudo apt-get remove python2.5-minimal
```
```
sudo apt-get update
```

---

### Post by lukeiamyourfather on 2009-07-10
Have you modified or removed the original Python installation, for example installing a new version of Python over the original?

---

### Post by emax on 2009-08-03
> **leoquant said:**
> ```
sudo apt-get remove python2.5-minimal
```
```
sudo apt-get update
```

Same problem here.

Running these suggested commands wants to remove half my system!!

```

This should NOT be done unless you know exactly what you are doing!
  python-minimal python2.5-minimal (due to python-minimal)
0 upgraded, 0 newly installed, 245 to remove and 16 not upgraded.
2 not fully installed or removed.
After this operation, 662MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase ‘Yes, do as I say!’
 ?] 

```

---


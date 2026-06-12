---
title: "Suggest any disk cleaner"
date: 2008-08-28
forum: General Help
---

### Post by ranjithnair on 2008-08-28
In windows i used disk cleaners such as registry cleaner,ccleaner etc..in ubuntu i have lot of junk to clean...can anybody suggest any software or the commands for cleaning

---

### Post by Kevbert on 2008-08-28
Try using 
```
sudo apt-get autoclean
```
in terminal and for (in) firefox, select Tools-Clear Private Data.

---

### Post by ranjithnair on 2008-08-28
not very effective...can you suggest any gui software

---

### Post by oilchangeguy on 2008-08-28
> **ranjithnair said:**
> In windows i used disk cleaners such as registry cleaner,ccleaner etc..in ubuntu i have lot of junk to clean...can anybody suggest any software or the commands for cleaning

define junk. and you can always backup your data and do a fresh install.

---

### Post by anotherdisciple on 2008-08-28
I just asked a similar question... it doesn't provide any speed boost to clean the gconf-editor (the closest thing in ubuntu to the registry). If you want to clean out old packages... do like they said above.

```
sudo aptitude autoclean
```

---

### Post by SammerHammer on 2008-08-28
KDE4 comes with an apps called Sweeper, which is very good IMO.

---

### Post by WRDN on 2008-08-28
Aswell as the commands already provided:

```
sudo apt-get clean
```

This removes all packages from the cache (/var/cache/apt/archive).

```
sudo apt-get autoremove
```

This removes unneeded packages.

```
sudo (apt-get install) localepurge
```

This package must first be installed, and it used to remove unneeded locales. After other packages are installed in the future, it is run automatically, and it removes the locales that may have been installed

You can also remove residual packages (i.e. those left behind after uninstalling a program) by opening Synaptic Package Manager, clicking the Status button, and then selecting "Not Installed (Residual)".

---

### Post by Kevbert on 2008-08-29
Related to this post.  
How do I remove old backup files in my home directory and it's subdirectories?  For example, if I edit .conkyrc it produces a backup .conkyrc~. After a while there can be loads of files (ending in ~).

---

### Post by Vivaldi Gloria on 2008-08-29
ranjithnair, see my post here:

[http://ubuntuforums.org/showthread.php?t=903493](http://ubuntuforums.org/showthread.php?t=903493)

> **Kevbert said:**
> How do I remove old backup files in my home directory and it's subdirectories?  

Open a terminal and give the command

```
find ~ -name "*~" -exec rm -f {} \;
```

to delete them. First test with

```
find ~ -name "*~" -exec echo {} \;
```

---


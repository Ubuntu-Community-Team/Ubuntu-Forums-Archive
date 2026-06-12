---
title: "Is there a way to upgrade all my software apps?"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by Macfunky on 2009-05-26
I heard there was an easy way to upgrade all my software to the latest versions in one easy step. How do i do this?

---

### Post by livestockPimp on 2009-05-26
"apt-get update"
from command prompt will update apt to the latest packages for your current distro.

"apt-get upgrade" will install all the latest updates.

---

### Post by livestockPimp on 2009-05-26
also, if you want to upgrade your distribution then after this is all up to date you can change your repositories by editing "/etc/apt/sources.list"
and then running and "apt-get update && apt-get dist-upgrade"

all these commands have to be entered as root or with sudo.

---

### Post by schmengei on 2009-05-26
I have 86 updates waiting to be installed, and can't do it because i receive the following msg when attempt is made. Can someone talk me step by step on what to do and where to go. My computer has really bogged down speedwise. Thanks in advance. When i go to terminal and manually attempt - nothing happens This is what pops up:



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

---

### Post by abn91c on 2009-05-26
> **schmengei said:**
> I have 86 updates waiting to be installed, and can't do it because i receive the following msg when attempt is made. Can someone talk me step by step on what to do and where to go. My computer has really bogged down speedwise. Thanks in advance. When i go to terminal and manually attempt - nothing happens This is what pops up:



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.
```
sudo dpkg --configure -a
```
then```
sudo apt-get update
sudo apt-get upgrade
```

---


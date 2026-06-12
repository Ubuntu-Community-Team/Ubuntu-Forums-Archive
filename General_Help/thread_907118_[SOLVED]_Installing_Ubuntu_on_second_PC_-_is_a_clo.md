---
title: "[SOLVED] Installing Ubuntu on second PC - is a cloning a better option?"
date: 2008-09-01
forum: General Help
---

### Post by b9k9kiwi on 2008-09-01
I am happily running Ubuntu on a purpose built PC but I have also installed Ubuntu (dual boot) on my Windows XP machine.  Of course, now Ubuntu 2 wants to download 511MB of updates which I have already downloaded to Ubuntu 1 - I am wondering if there is a way to avoid this waste of bandwidth.

Perhaps I could clone Ubuntu 1 to Ubuntu 2 - is this possible?

---

### Post by forger on 2008-09-01
Don't need to clone anything.
If you updated Ubuntu 1 successfully, you can use [aptoncd]("apt://aptoncd") - you can install it by clicking on the url or by executing the following command in terminal:
```
sudo apt-get install aptoncd
```
Once it's installed, run it from System > Administration > AptOnCD

If you want the "manual" way, Ubuntu caches the downloaded .deb packages at **/var/cache/apt/archives/**
You can copy the files to Ubuntu 2 and execute
```
sudo apt-get update
```
This will refresh the package database and you're good to go!

---

### Post by b9k9kiwi on 2008-09-01
> **forger said:**
> Don't need to clone anything.
...
This will refresh the package database and you're good to go!

Thank you.

---


---
title: "upgrading to 8.04.2 maintenance release"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by mfox on 2009-01-23
I have 8.04.1 installed and was wondering if I already have the equivalent to 8.04.2 if I have been doing regular updates?  If not, is there some way to upgrade 8.04.1 to 8.04.2 without having to reinstall?

---

### Post by Magnes on 2009-01-23
> **mfox said:**
> I already have the equivalent to 8.04.2 if I have been doing regular updates??

Yes, you have.

---

### Post by ajgreeny on 2009-01-23
You can always check this with **cat /etc/lsb-release** in terminal.
```
xxxxxxx@ubuntu804:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"
xxxxxxx@ubuntu804:~$ 
```

---

### Post by mfox on 2009-01-23
Thanks, ajgreeny; I didn't know about that file.  And yes, I do have 8.04.2 installed.

---

### Post by TitanTiger on 2009-01-27
I ran that command in the terminal and have 8.04.1 as my version.  Is there any reason to upgrade to 8.04.2?

---

### Post by mfox on 2009-02-08
It's probably a good idea to use the Update Manager to update your software, as there could be useful bug fixes or security fixes posted since you installed your system.

---

### Post by Phil Urich on 2009-06-15
I've been keeping up to date (in fact I just downloaded some updates a minute ago!), but "cat /etc/lsb-release" still says 8.04.1 for me . . .

---


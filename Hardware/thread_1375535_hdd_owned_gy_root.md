---
title: "hdd owned gy root"
date: 2010-01-08
forum: Hardware
---

### Post by tad1073 on 2010-01-08
how do I change the permissions to folder and files on a hdd that is owed by root?

```
drwxrwxrwx  1 root root 4.0K 2010-01-07 17:41 FamilyFiles
``````
drwxrwxrwx 1 root root    0 2009-07-21 09:22 DadsFiles
drwxrwxrwx 1 root root  84K 2010-01-05 19:41 FFRS
drwxrwxrwx 1 root root 4.0K 2009-09-02 14:38 LinzisFiles
drwxrwxrwx 1 root root  16K 2010-01-05 23:05 Media
drwxrwxrwx 1 root root 4.0K 2010-01-07 10:34 TadsFiles
drwxrwxrwx 1 root root    0 2010-01-06 19:44 W7BackUp

```cat /etc/fstab
```
/dev/sdb1 /media/FamilyFiles ntfs-3g defaults,locale=en_US.UTF-8 0 0
```
I need to take ownership of the aforementioned drive so I can create user shares that are accessible only by the assigned people.

---

### Post by tad1073 on 2010-01-09
could the mod's change the title of this post to "hdd owned by root"
bump

---

### Post by NoaHall on 2010-01-09
chown -R /media/FamilyFiles

---

### Post by tad1073 on 2010-01-09
I have tried that but it doesn't seem to work.

```
UUID=WhatEverTheUUIDOfTheDiskIs /media/FamilyFiles ntfs-3g
rw,user,auto,umask=002,uid=1000,gid=100,locale=en_US.utf8   0    0

```seems to work for now

---

### Post by tad1073 on 2010-01-09
I have managed to take ownership of the files on the FamilyFiles drive. I mapped a network drive on xphome under my moms profile, but to connect to the drive I have to put in my username and password. How do I change it so that each members folder can be mounted with their username and password?

---


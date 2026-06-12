---
title: "i just installed ubuntu on an NTFS partition"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by excbuntu on 2009-01-30
eee 1000HA. i'm a newbie from windows, so i don't know what i'm doing. but everything seems to work perfectly. i mounted the easypeasy iso via daemontoolz in windows xp and installed it so i now have a dual boot system. everything was pretty much automated by the cd. all i did was select the empty ntfs partition and confirmed.

after this install, i read a few things about filesystems and such, and i found out that, in general, linux cannot be installed on an ntfs filesystem. so how was i successful? i feel like i should have deleted the partition and formated it to ext3 via the installation cd. i'm not complaining about the speed right now cause the OS feels really responsive and solid, but perhaps things would be faster if easpeasy was installed on ext3?

what do you guys think? btw, first post!

---

### Post by PmDematagoda on 2009-01-30
I don't think Ubuntu would work like that at all, so most likely the installer automatically formatted the partition to Ext3 when you installed it. If you take a look at:-
```
cat /etc/fstab
```
then it most likely has ext3.

---

### Post by Elfy on 2009-01-30
Unless you installed it with wubi - which it appears to be > i mounted the easypeasy iso via daemontoolz in windows xp

That creates a virtual partition for ubuntu to use in general terms. So it is a dualboot - but not in the conventional sense

---

### Post by excbuntu on 2009-01-30
> **forestpixie said:**
> Unless you installed it with wubi - which it appears to be 

That creates a virtual partition for ubuntu to use in general terms. So it is a dualboot - but not in the conventional sense

hmm. i'm not sure if i understand. it didn't create any partition. i installed it on the empty ntfs d: drive that was already there. and i am dual booting, but what conventional sense are you talking about?

---

### Post by jrusso2 on 2009-01-30
I am pretty sure it formatted it ext3 before install. If not you will have lots of problems.  NTFS doesn't do Linux permissions.

---

### Post by Elfy on 2009-01-31
> **excbuntu said:**
> hmm. i'm not sure if i understand. it didn't create any partition. i installed it on the empty ntfs d: drive that was already there. and i am dual booting, but what conventional sense are you talking about?

It created a virtual partition and you can move it to a real partition later with LVPM.

By conventional sense I mean that you make seperate partitions for the installer to use. If you delete your windows installation then you will lose ubuntu.

---


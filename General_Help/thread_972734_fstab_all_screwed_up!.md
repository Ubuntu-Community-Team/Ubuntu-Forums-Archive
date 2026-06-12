---
title: "fstab all screwed up!"
date: 2008-11-06
forum: General Help
---

### Post by bilijoe on 2008-11-06
Is there any way to get the system to regenerate fstab?  Mine is totally screwed up--seems to be describing another computer entirely.  Although everything seems to work, the system thinks that / is 100% full (it's not) and that it is 13Gb in size (it's 20), and it thinks that my home partition (a separate partition) is 75% used (actually about 6%) and is 10GB in size (it's 200Gb).  

My system runs from a SATA HDD which is seen as sdb, but fstab makes no mention of sdb, only sda, which is in the system, but doesn't get mounted at boot time, only when I click on its icon, which is the way I intended it.  So except for thinking that / is smaller than it is and full, and that /home is MUCH smaller than it is, and 75% full, the system works OK, except I often get the kind of sluggish performance you'd expect from a nearly full HDD, though this one is no where near full.  

I really don't want to have to educate myself to the point where I can create a proper fstab myself--I'd rather re-install.  Since the system generates fstab during an install, it stands to reason that there is a utility somewhere that does that--generates a (proper) fstab.  Ant help out there? :confused:

---

### Post by jpkotta on 2008-11-06
I don't know the details of the Ubuntu installer, but if I had to guess I'd say that fstab is generated right away with info from the partitioner.  In otherwords, it's not part of a package you can reinstall.
```
$ dpkg -S /etc/fstab
dpkg: /etc/fstab not found.
```

It sounds like all you need to do is change the device nodes, which shouldn't be so bad.  

```
man fstab
```

---


---
title: "Synaptic error - problem parsing dependancy"
date: 2008-10-12
forum: General Help
---

### Post by clint1010 on 2008-10-12
Could someone please tell me what the following error report means. It occurs when I try to open Synaptic package manager, and I'm unable to update my system. Running 32bit 8.04 on a Toshiba laptop.

> E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

And if I run the update manager (similar thing I guess) I get the following error

> Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


I'll check the /etc/apt/sources.list file to see if there is anything obvious

Anyone else have this before? This laptop is has been faultless with 8.04 till this problem, need assistance.

Thanks

---

### Post by drs305 on 2008-10-12
I would bet it has something to do with the spelling of "hardy" in the preceeding:
```

E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_**harty**_all_binary-i386_Packages

```

Open your sources.list, correct the typo, and reload the sources. 
```

cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list

```

If you don't see the typo there go to /var/lib/apt/lists, find the same listing and rename it with 'hardy'.
```

gksudo nautilus /var/lib/apt/lists

```

---

### Post by clint1010 on 2008-10-13
will have a look at that, thanks for your reply

---

### Post by redsox59 on 2008-10-13
I just had the same issue and wanted to say that there was a typo in /etc/apt/sources.list just as was suggested above. Fixed the type and then I was able to update as normal.

---

### Post by albesan on 2008-10-13
yep, thanks, worked for me too.

a.

---

### Post by zentus on 2009-05-12
worked like a charm - thank you!

---

### Post by eumetaxas on 2010-12-05
Thank you, even if it is 2 years after this post!

---


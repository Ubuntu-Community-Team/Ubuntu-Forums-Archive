---
title: "hard drive fsck issue"
date: 2008-11-18
forum: General Help
---

### Post by sigurnjak on 2008-11-18
This is log of fsck after pc froze . 

Log of fsck -C3 -R -A -a 
Tue Nov 18 18:26:12 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda7 was not cleanly unmounted, check forced.
/dev/sda7: Entry 'file:%2F%2F%2Fhome%2Fandrey%2FDesktop.xml' in /andrey/.nautilus/metafiles (3145731) has deleted/unused inode 15761427.  CLEARED.
/dev/sda7: Entry 'patterns.ini' in /andrey/.mozilla/firefox/4h4x1yr3.default/adblockplus (3933353) has deleted/unused inode 3932163.  CLEARED.
/dev/sda7: Entry 'prefs.js' in /andrey/.mozilla/firefox/4h4x1yr3.default (3933348) has deleted/unused inode 3934737.  CLEARED.
/dev/sda7: Entry '952FEA71d01' in /andrey/.mozilla/firefox/4h4x1yr3.default/Cache (14401547) has deleted/unused inode 14402137.  CLEARED.
/dev/sda7: Unattached inode 3932184


/dev/sda7: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Tue Nov 18 18:31:27 2008
----------------


How do i proceed safely from here?:confused:

---

### Post by dcstar on 2008-11-19
> **sigurnjak said:**
> This is log of fsck after pc froze . 
.......
/dev/sda7: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
........
How do i proceed safely from here?:confused:

Boot off a live CD, find the appropriate partition of your disk, and in a terminal then:

```
fsck /dev/whatever -y
```

---

### Post by sigurnjak on 2008-11-19
Thank you ! All fixed !:)

---


---
title: "Upgrade to 9.04 does not find 8.10"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2009-07-08
I downloaded the 9.04 AMD 64 ISO, burned the CD and attempted to install it along with my present 8.04

However, it did not report finding 8.04 with all of my settings and data, but only an old SUSE 11.0 which was on another disk partition. Therefore, not wanting to lose everything I cancelled the update.

This is strange behavior for Ubuntu, and I am at a loss to explain or circumvent this for another attempt.

---

### Post by cariboo on 2009-07-08
In order to update from 8.04 to 9.04, you first have to update to 8.10, as there is no direct update path to 9.04. Before you start your ugrade, disable any third party repositories and ppas. Then press Alt-F2 and type:

```
update-manager -d
```

This should start the upgrade process to 8.10. Once the upgrade is finished, make sure you have the cdrom enabled in /etc/apt/sources list. The easiest way to do this is to open Synaptic, and go to Settings-->repositories, and place a check mark beside cdrom. The type:

```
update-manager -d
```

The upgrade process shpuld start again for Jaunty.

---

### Post by Oldhacker on 2009-07-08
Thank you for the response. However, I am already running 8.10, not 8.04. My heading for this thread was correct but I made a typo in the body.

When I reached the partitioning stage in my attempt to upgrade, it showed all of my existing OS's including SUSE 11.0, Ubuntu 8.04 and Ubuntu 8.10
But when I tried the default partitioning offered, that was when it said that there were no OS's found to import data from. ???

---

### Post by Oldhacker on 2009-07-09
I thought that I had found the solution when I specified my other physical hard disk this morning and it showed all of my existing operating systems.
I selected the "keep all OS's and choose between them side by side" option, which is what I want.

However, when I continued into the partitioning,
it still said that there were no other users or OS's to import data or settings from!

I am giving up on Ubuntu 9.04 and can only hope that the next edition will have the ability to import my data and settings as it has done in the past.

---


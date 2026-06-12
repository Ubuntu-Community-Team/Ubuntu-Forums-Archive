---
title: "Raid partition option not available to choose"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by jaredheath on 2009-06-27
New to Ubuntu...previously used SUSE.  I am trying to install on a system with 3 disks, one I will use as the primary boot drive and 2 I intend to do a Raid 0 on.

The option in the partition app to create a raid space is simply not there.  I cannot find any reference anywhere as to how or why this would be the case.

What am I missing here?

---

### Post by ronparent on 2009-06-28
I think that what you are encountering is trying to use the standard live cd out of the box to install the system and create the raid drives. The live cd contains no raid support. For that you have to use the alternate cd which is downloaded from the same site. 

If the non raid drive is what you are installing to, it would be possible to leave the terget drives for raid as unallocated space. You would then be able to install the raid software after booting into the newly installed system and use it to configure or discover your raid0. Once activated the drives can be normally patitioned using the partition manager. You would fo course be completely on your own to mount any raid0 drives for use by your system.

The main immediate issue is whether you plan on using fakeraid or software raid? You should read up on them, or at least your choice prior to plunging in.

---


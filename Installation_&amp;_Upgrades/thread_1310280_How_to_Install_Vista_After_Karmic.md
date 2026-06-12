---
title: "How to Install Vista After Karmic"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Putnam11 on 2009-11-01
I need to install Vista as an extra boot option. I have the Windoes boot disk, gave 20 GB's to an un-allocated partition, and now what?
I have both a Vista CD and a 9.04 LiveCD.
I am running Karmic 9.10 with all current updates.
Sticking the Windoes CD in I can't do anything as it doesn't recognize the unallocated space or something :S

Please walk me through it, I have a craving for some online poker.

---

### Post by Putnam11 on 2009-11-03
bump

---

### Post by enderwig on 2009-11-03
Windows is greedy, you have to install it first, then add ubuntu to the box after windows is properly installed.

---

### Post by Unknown Pirate on 2009-11-03
1. Install Windows
2. Install Ubuntu with **Dual Boot** installation.
3. Done.

---

### Post by mcooke1 on 2009-11-03
Reinstall vista defrag a few times use windows disk management to shrink the partition that vista was installed to then install ubuntu to the free space created.

---

### Post by phillw on 2009-11-03
> **Putnam11 said:**
> I need to install Vista as an extra boot option. I have the Windoes boot disk, gave 20 GB's to an un-allocated partition, and now what?
I have both a Vista CD and a 9.04 LiveCD.
I am running Karmic 9.10 with all current updates.
Sticking the Windoes CD in I can't do anything as it doesn't recognize the unallocated space or something :S

Please walk me through it, I have a craving for some online poker.


Hi,

the best I've read for all things dual booting is here ...

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

They cover about every scenario with plenty of screen shots.

hope that helps,

Phill.

---

### Post by sadaka on 2009-11-04
Theoretically:
1. For free space that you have, create a NTFS partition in ubuntu
2. Boot from vista cd and install it, I guess its installer should see the NTFS partition
3. Repair MBR with Ubuntu install CD to use GRUB (Vista will screw up your MBR)

I have done smth like this few yars ago with XP and other linux distro

IMFAO, it would be better to install vista into nearest trash container, though ;)

---


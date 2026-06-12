---
title: "How Do I Uninstall Ubuntu from Windows dual boot"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by darylt on 2009-11-02
Hi,
 
Bit of an odd request but I need to remove Ubuntu from my laptop which is installed alongside Windows Vista and restore the MBR to boot from Windows.
 
I am going to put a separate 2nd HDD in to install Ubuntu on as I didn't have enough room on the first.
 
Daryl

---

### Post by pastalavista on 2009-11-02
> **darylt said:**
> Hi,
 
Bit of an odd request but I need to remove Ubuntu from my laptop which is installed alongside Windows Vista and restore the MBR to boot from Windows.
 
I am going to put a separate 2nd HDD in to install Ubuntu on as I didn't have enough room on the first.
 
Daryl

You'll have to boot from a live CD disk partitioner (Ubuntu live CD will work.. System-> Administration-> gparted - Partition Editor). Delete the Ubuntu partition and expand the Windows partition to reclaim the space.

Then you'll need a Windows install CD to repair the Windows bootloader. At the command prompt, enter 'fixboot' or 'fixmbr'

---


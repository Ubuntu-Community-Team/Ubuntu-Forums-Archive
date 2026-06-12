---
title: "upgrading 7.10 to 9.04 -&gt; lost superblock on raid-0 array"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by remi_2 on 2009-09-07
Hi guys, 
I'm facing an unexpected difficulty with a raid-0 array made of two disks.

The computer was running 7.10. It has three drives, one for the root '/'  and the two others assembled in RAID-0 for /home. 


I formatted the '/' drive to do a fresh 9.04 install, keeping the RAID drives untouched. 

upon installation, the installer asked if I wanted to activate the LVM for the RAID array that had been detected. I typed yes.

after logon, all I could see in gparted was en empty block device listed under /dev/mapper/<seemingly random ID>, whereas normally it shows up as /dev/md0 with data intact on it.

I used mdadm to try to reasseble the array by hand, and it aborted, telling me the devices had no valid superblock.

Is there anything else I can try to recover my partition before reformatting the drives?

---


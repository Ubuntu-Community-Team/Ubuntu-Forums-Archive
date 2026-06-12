---
title: "zajactyj busy box error/ help"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by zajactyj on 2009-03-24
alright guys and gals, 
i did a fresh download about an hour ago, i have been using the live cd becuase that is the only thing that seems to work. 
downloaded without a flaw, it told me to restart the computer and remove the disk. I restarted and i get this.,,

boot from (hd0,5) ext 3    3e3eb19b-99ad-4b81-861c-cb96c300d051b
starting up ...
   aperature pointing to e820 ram. ignoring. 
   your bios doesn;t leace a aperture memory hole 
   please enable the iommu option in the bios setup 
   this costs you 64mb of ram 
loading, please wait...
 - boot args (cat/proc/cmdline)
   -check rootdelay= (did the system wait long enough?)
   -check root= (did the system wait for the right device?)
 -missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/3e3eb19b-99ad-4b81-861c-cb96c30d051b does not exist. dropping to a shell!

busybox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
enter 'help' for a list of built-in commands.

thanks in advance for any input:
my build 
xfx geforce 8200 mobo 
sata hdd 
8gb ram 
amd 64x quad core 
iam using 64x desktop edition

Any ideas people?

---


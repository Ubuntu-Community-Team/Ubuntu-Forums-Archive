---
title: "Unable to Access / Format Extended Drive"
date: 2005-11-07
forum: General Help
---

### Post by tagg3rx on 2005-11-07
Hi All  Need some help here - it appears 95% of my harddisk is unformatted and inaccessable.

I have a 10 gig HD 
In system - admin - disks 
it shows my hd partitioned into 2 drives (1 and 5)
/dev/hda1 looks fine but is only 243 MB
/dev/hda5 says its unformatted and inaccessible

I do a sudo cfdisk
and get 2 Harddrives listed hda1 and hda5
I select
hda5 (blank) Logical Linux LVM (blank) 997.27
Select write as it seems the closest to format

It says Wrote Partition table, but re-read table failed reboot to update table

So I rebooted

Loaded up system - admin - disks
Choose Hard disk > Partitions tab and have 2 partitions hda1 looks fine
hda5 indicates:
access path none (i have tried changing to home)
size 9.29 GiB (free space not avial)
Status Inaccessible

I have clicked format and a status bar jumps to 100% but nothing happens
I have clicked enable and it goes grey but comes back the same

So how do I format this drive (and make it the default place where I save data)

Thanks ubuntus
:KS Tagg3rX :KS

---

### Post by tagg3rx on 2005-11-07
*bump* 
Help Please

---

### Post by RAOF on 2005-11-07
It looks like your drive is set up to be a part of a LVM - logical volume management - group.  This means that you should be able to extend your existing partitions onto it (and, if you add a new disc later, onto the new disc as well).  I'm not familiar with it, but here's a (not particularly basic) [howto]("http://www.tldp.org/HOWTO/LVM-HOWTO/") I've seen posted on these boards.

And [this]("http://patrick.wagstrom.net/weblog/linux/mythtv/mythtv-lvm.xml") seems to be a fairly straightforward example of doing it in ubuntu.

---


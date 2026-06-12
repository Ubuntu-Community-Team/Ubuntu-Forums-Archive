---
title: "Sever Installation HD partition  question?"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by ndnd on 2009-01-15
Hi,
I am a bit new to Linux O.S 

This is my 2nd install of linux Server O.S and I am stuck at HD partition 

I am at the Disk Partition Stage
Capacity for HD is 2.5TB (6x500GB HD Raid 5) as we had discussed. However, during partition stage I get

> 
SCSI1 (2,0,0) (sda) - 1.9TB DELL PERC 6/i
#1 primary 82.2 MB   fat16
#2 primary  2.2 GB B fat32
    pri/log     1.9 TB     FREE SPACE
 
SCSI (2,1,0) (sdb) - 610.4 GB DELL PERC 6/i
    pri/log      610.4 GB  FREE SPACE



I need to setup this way
> 
/boot     -   1 GB - (Boot Partition)

/            -   8 GB   (root Partition)

/swap    -   8 GB    (twice the size of RAM)

/data     -  2.4 TB (The rest of the free space available in the HDD)


My question why is there 'sdb' and 'sda' and is there a simple way to have a single HD of 2.5 TB that I can partition?

---


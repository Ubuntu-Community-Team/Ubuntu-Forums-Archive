---
title: "Help on setting up RAID 5 on  Ubuntu Server 8.10"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by solo23 on 2008-12-04
I just setup a ubuntu 8.10 server with a 3 80GB Hard drive RAID 5. I read that GRUB won't boot the system correctly on a RAID 5 so what I did was partition all 3 drives with a small 250 mb primary partition and created a RAID 1 and formatted it as ext3 and put /boot there. With the remaining disk space I created a logical partition in each drive and set that up as a RAID 5. I setup a 2g swap partition on the RAID 5 and the with the 148g left over created a logical volume and formated it as XFS for the system.

Needless to say, it surprised the hell out of me when the system booted up. I already have my Samba server running on it with no problems.

My question is, is this correct? 

If a drive fails do i have to just set up my 2 different physical RAID partitions on the replacement drive for the system to rebuilt the RAID 1 and RAID 5 partions?

---

### Post by jaygo on 2008-12-28
I believe you can just plug in a blank drive and it will take care of the formatting & partitioning. The only part in question is how mdadm will handle the rebuild of both RAID 1 & RAID 5 on the same disk ... I'm not that familiar with it.

---


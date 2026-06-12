---
title: "Installation not seeing partitions"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by Elemen7s on 2009-09-27
I would like to install ubuntu 9.04 which will be the main OS.

On step 3 I choose the manual option. 
On step 4, the partitions that already exist are not visible. 

How can i get those partitions visible 

Thanks for reading

---

### Post by louieb on 2009-09-27
You may have a non-standard partition table. Installer detects that and shows a blank drive.

If you have internet with the live CD please put the partition table in your next post.
Open applications>accessories>terminal 

```
sudo fdisk -l
``` lowercase L at the end. 
Cut and paste the output in your next post.

---


---
title: "manual partition step when installing 8.04"
date: 2008-07-18
forum: General Help
---

### Post by supershin on 2008-07-18
I have a dual boot setup with 7.04 and XP and I want to install 8.04 on the partition that has 7.04. When running the 8.04 liveCD, I reach the manual partition stage and i'm not sure what to choose. I really don't want to have to reinstall everything. 
  It has 2 ntfs partitions, C(XP) and D(data) drive, a 6GB partition for recovery or something and the ubuntu partition of 12GB and its swap. Reading some tutorial it had something about some boot partition so i'm not sure how that fits in, So how do I install 8.04 over 7.04? Just choose the 12GB linux partition and what about ext3 and those edit partition options?

---

### Post by overdrank on 2008-07-18
> **supershin said:**
> I have a dual boot setup with 7.04 and XP and I want to install 8.04 on the partition that has 7.04. When running the 8.04 liveCD, I reach the manual partition stage and i'm not sure what to choose. I really don't want to have to reinstall everything. 
  It has 2 ntfs partitions, C(XP) and D(data) drive, a 6GB partition for recovery or something and the ubuntu partition of 12GB and its swap. Reading some tutorial it had something about some boot partition so i'm not sure how that fits in, So how do I install 8.04 over 7.04? Just choose the 12GB linux partition and what about ext3 and those edit partition options?

Hi and yes just choose the 7.04 partition and then format it as ext3.

---

### Post by Shazaam on 2008-07-18
Yes you can install 8.04 on the 12gig partition (overwriting 7.04) if you are sure that is the one you want to install on. Just remember that when you do this all of the updates/apps installed on 7.04 will be gone. I would first run this in terminal and write down the partition information....
```
sudo fdisk -lu
```
(small L)
When Ubuntu is installing it will re-use/format the swap partition and will also ask if you want to migrate your user data.

---

### Post by supershin on 2008-07-18
So when I choose the 12GB linux partition and ext3 from the edit option, it'll automatically reuse/format the swap? That swap part and fdisk is a bit confusing and I want to be perfect clear about everything so as to avoid reinstalling everything.

---

### Post by cybrsaylr on 2008-07-19
Yes. There is a guide I read here somewhere here that states when you format your older Ubuntu partition, the new version 8.04 will automatically seek that same partition out and install there again.
They said this fresh install is better than upgrading online to 8.04 from the older version.

---

### Post by supershin on 2008-07-19
Cool. Thanks everyone.

---


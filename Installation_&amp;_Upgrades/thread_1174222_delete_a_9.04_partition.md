---
title: "delete a 9.04 partition"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2009-05-30
I had lost the installation of 9.04 when i installed windows. So i tried grub & failed. So reinstalled 9.04. Now i have 2 of then & need to delete the partition of the old 9.04. How do i do that? TIA

---

### Post by ExWindowsDude on 2009-05-30
> **jtmedin said:**
> I had lost the installation of 9.04 when i installed windows. So i tried grub & failed. So reinstalled 9.04. Now i have 2 of then & need to delete the partition of the old 9.04. How do i do that? TIA

bump! 

(I'm having the same problem)---Thanks!
(dual boot--with Win2k3).

---

### Post by Mark Phelps on 2009-05-31
> **jtmedin said:**
> I had lost the installation of 9.04 when i installed windows. So i tried grub & failed. So reinstalled 9.04. Now i have 2 of then & need to delete the partition of the old 9.04. How do i do that? TIA

You can boot from a LiveCD, start the Partition Editor, and remove the Ubuntu partitions you no longer need. Since you'll have more than one ext3 partition showing up in GParted, the ones you DON'T want to remove are the ones that have entries under "Mount Point".

---


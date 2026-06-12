---
title: "[SOLVED] Need to add apartition"
date: 2008-10-14
forum: General Help
---

### Post by TaskmasterC on 2008-10-14
I need to know if anyone can help me with a problem. I want to add a new partition to my drive so I can re add Vista. Problem is Ubuntu used all my HD. How can I repartition it without messing up Grub . I am running 2 HDD, one has XP sp3 exclusively, the other Ubuntu. I want to reinstall Vista on the second drive along with Ubuntu. Any help will be greatly appreciated.

---

### Post by tuxxy on 2008-10-14
You could shrink your current partition, then create a new partition for Vista with the space you created, to do this you would need to boot the Live CD of Ubuntu so that your disks are not mounted, allowing you to edit the partitions

Once booted open the application gparted, should be at system > admin > partition, you might want to take a look at a howto if your unsure about any aspect of the partition process.

---


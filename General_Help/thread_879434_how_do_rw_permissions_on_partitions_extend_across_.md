---
title: "how do rw permissions on partitions extend across Os'es"
date: 2008-08-04
forum: General Help
---

### Post by mc4man on 2008-08-04
i did a fresh install of hardy on sdb today and after it was set up I created 3 new partitions, 2 ext2 and 1 fat32. While i could immediately mount and unmount all 3 with l.click, r.click, only the fat32 could be written to. So i created a temp dir. to mount, chown the ext.2's as below which gave me the write permissions to them.

> sudo mkdir /media/fix
sudo mount /dev/sdb5 /media/fix
sudo chown doug:doug /media/fix
sudo umount /dev/sdb5 /media/fix
sudo mount /dev/sdb7 /media/fix
sudo chown doug:doug /media/fix
sudo umount /dev/sdb7 /media/fix
sudo rmdir /media/fix

When i booted into gutsy on sda I was surprised to see that I could write to the 2 new ext2's without doing anything.
 
Do the permissions/ownership 'stay' with the partitions?

---


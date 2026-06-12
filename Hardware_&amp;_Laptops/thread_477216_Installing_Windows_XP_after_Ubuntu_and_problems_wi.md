---
title: "Installing Windows XP after Ubuntu and problems with fstab"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by librano on 2007-06-18
Hi all!

When I installed Ubuntu I manually partitioned my hard disk creating the swap partition first at the end of my hard disk and then filling the rest with my Ubuntu root partition. Because of this, hda1 (swap) was at the end of the hard disk and hda2 (root) at the beginning. 

Later on I created a third partition in between hda2 and hda1 which was hda3. I installed Winodws XP to this partition but somehow this changed the partition names and put them in order... ie before installing Windows the order of the partitions were hda2 (Ubuntu root), hda3 (New partition for Windows) and hda1 (swap). After the installation of Windows XP this is how it is now; hda1 (Ubuntu root), hda2 (Windows XP) and hda3 (swap).

This does not cause any problems in normal use (once i modify /etc/fstab). However, after any kernel upgrades I have to redo the changes in fstab so that grub points to the right partitions and I have to add Windows XP again. I suppose the old partition names are stored in a backup file from which the they are retrieved during a kernel update.

How can I correct this so that grub updates fstab correctly and does not remove Windows XP from the boot options?

Thanks you in advance.

p.s. I am using Edgy which was upgraded from Dapper. I installed Windows while I was using Dapper.

---


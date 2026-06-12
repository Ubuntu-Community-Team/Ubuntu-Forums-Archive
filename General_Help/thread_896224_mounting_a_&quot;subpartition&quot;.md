---
title: "mounting a &quot;subpartition&quot;?"
date: 2008-08-21
forum: General Help
---

### Post by pixeltecs on 2008-08-21
Okay, this seems weird to me but I assume there is a way to do this.  I recently switched to ubuntu from windows and setup KVM and virt-manager so I could install windows XP (I still need a tether to the windows world).  virt-manager gives you an option to add a drive to the virtual machine.  You have an option to use a block device (partition) or a file.  I have a spare partition that I want to format with fat32 for sharing of files between the two OSs.  I would prefer not to use a network drive.  So, I mounted the drive and partitioned it and formatted in XP.

My problem is that I can't seem to mount this in linux.  What is strange is that my drive is /dev/sda.  The partition I gave to windows is /dev/sda1.  When I load windows, it then partitions the "virtual" drive.  This essentially creates a "subpartition".  In linux if I fdisk /dev/sda1, I see a partition for /dev/sda1p1.  I don't have a device for this in /dev.  Is there a way to create one or a way to do some sort of loopback on /dev/sda1 to access /dev/sda1p1?

If not, is there a better way to share files between a virtual host and guest through a filesystem (not networking)?

Thanks for any assistance!

--Phil

---


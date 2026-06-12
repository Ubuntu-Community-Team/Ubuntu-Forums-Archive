---
title: "Add existing raid arrays to ubuntu"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by mganapa on 2009-08-21
Hello All, 
I have a RAID 1 array from an OpenFiler installation I had been using. Both the disks have been formatted with XFS file system and are SATA 2 drives. I now have a new machine with Ubuntu 9.04 Server edition. I would like to move this raid array to the new Ubuntu server without loosing data. I tried connecting the drives during installation but Ubuntu partition manager shows one device to be a member of an LVM  while the other is listed under regular SCSI devices. 
I have now gone ahead and disconnected the drives and completed my Ubuntu installation. I would however like to add these two drives without loosing the data in them. Any pointers?

---

### Post by mganapa on 2009-08-22
Hello All, 
Did a lot of google search and finally found the following two sites that helped me solve this issue:
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)
[http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server](http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server)

Apparently, OpenFiler user LVM by default and my RAID 1 disks were a part of an LVM I had created  with openfiler. Install the following packages:
lvm2 (installs watershed as dependency)
mdadm (install postfix packages as dependency)

Once I got these two installed, I ran the following commands
fstab -l : Told me that my raid device was under /dev/md0 and mdadm was running
mdadm --detail /dev/md0 : Informed me that my RAID arrays were working and the members were /dev/sda1 and /dev/sdc1
vgscan : Identified my LV as rd1d0
vgchange -ay rd1d0 : Activated my LV rd1d0
mount /dev/mapper/rd1d0 /mnt/rd1d0 : mounted my LVM based RAID 1 device
blkid : Identified the UUID used by the RAID 1 LV array
Finally I edited fstab to include the storage to mount at /mnt/rd1d0 at boot. Used the UUID obtained in the last step to make the entry in fstab consistent with Ubuntu's entry

---


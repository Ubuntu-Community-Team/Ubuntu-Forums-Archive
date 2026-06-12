---
title: "fsck -a"
date: 2008-07-17
forum: General Help
---

### Post by deb_untu on 2008-07-17
After installation of PCOSlinux on another partition ubuntu fails to mount the swap partition(dev/sda9) on boot.

On using command   [COLOR=Red]swapon -a[/COLOR] the following message is displayed.
swapon: cannot stat /dev/disk/by-uuid/1b258d63-094a-4303-8411-7a4397df882b/dev/sda9: No such file or directory


Also, I could see following  error message on boot. 

/dev/sda8: 25326 files, 485479/509055 clusters
fsck.ext2: Unable to resolve 'UUID=8dddbc0a-c178-41e7-b008-e2a5ee31c51e'

/dev/sda8  is a vfat(FAT32) partition. fsck -a couldn´t solve the problem.

---

### Post by mcduck on 2008-07-17
While installing PCOSLinux you have changed some of the partitions, which also means that their UUID's have changed as well.

You should get the new UUIDs (with the 'blkid'-command) and edit your /etc/fstab to reflect the changes.

For the FAT32 partition, you should probably disable fsck for it completely. It's not going to do much good anyway. Change the last number on that partitions entry in fstab to "0".

(If you need more help with this, please run "blkid" and "sudo fdisk -l", and post the outputs together with the contents of your /etc/fstab here.)

---


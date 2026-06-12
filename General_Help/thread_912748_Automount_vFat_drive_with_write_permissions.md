---
title: "Automount vFat drive with write permissions?"
date: 2008-09-07
forum: General Help
---

### Post by danrulz98 on 2008-09-07
I have a laptop with an 80 GB drive. The drive is split up into 5 partitions, a 20GB windows partition (ntfs), a 20GB Ubuntu partition, and a 40GB partition (fat32) that is seen by both. 
In Windows, the 40GB partition is used as the root for the "My Documents" folder and has everything important on it. 
I have been trying to get it to mount automatically in Ubuntu 8.04. I have managed that by adding an entry to fstab
> 
/dev/sda5 /media/bridgedisk vfat iocharset=utf8,umask=000 0 0


It does mount /dev/sda5 as /media/bridgedisk, but as read-only.

How can I automount it with write permissions for all users?

---

### Post by danrulz98 on 2008-09-14
Hmm...
chmod -R 777 /media/bridgedisk

---


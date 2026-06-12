---
title: "can't mount a partition?"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by furtivefelon on 2005-06-15
i have this logic partition contains vmware image for windows (from my previous mepis installation).. i don't want to format it.. and i can see it in qtparted, i can't mount it for some reason, when i type sudo mount /dev/sda5, it says mount: can't find /dev/hda5 in /etc/fstab or /etc/mtab... i'm sure the name is right.. how do you make ubuntu recognize the partition?

---

### Post by GTvulse on 2005-06-15
By explicitly assigning a mount point. If there is no default mount point defined in /etc/fstab it won't happen automatically. ```
sudo mount -t <filesystem type> /dev/hda5 /mnt/my_mount_point
``` will do the trick. BTW, is it /dev/sda or /dev/hda? The first is a SCSI disk the second an IDE disk.

---


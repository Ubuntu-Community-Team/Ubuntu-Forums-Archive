---
title: "Can not create btrfs subvolume need help"
date: 2021-01-26
forum: Hardware
---

### Post by lance bermudez on 2021-01-26
I have the read out from the lsblk, blkid, mount and cat /etc/fstab in the attached file.

# btrfs subvolume create /home/1tb
ERROR: target path already exists: /home/1tb

# btrfs subv list /home/1tb
#[ATTACH]287824[/ATTACH]# blank return
# btrfs subv list /
ERROR: not a btrfs filesystem: /
ERROR: can't access '/'

---


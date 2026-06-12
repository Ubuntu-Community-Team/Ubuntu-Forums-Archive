---
title: "Mdadm-RAID, dmcrypt and/or btrfs"
date: 2014-05-23
forum: Hardware
---

### Post by kristianz on 2014-05-23
Hey!

Can anyone help me with suggestions for a good choice of software stack on my hard drives that achieves the following:

* RAID-like redundancy
* Encryption
* Modern filesystem features like checksumming and bitrot recovery, snapshots and ease of resizing subvolums


Currently I have a stack like this:

Mdadm-RAID 5 (three drives, on of which is for redundancy) -> dmcrypt/LUKS -> LVM -> Ext4

but as I'm planning to upgrade my drives it, I'd like to use the opportunity to move to btrfs. I'd like to include the old drives as a nested RAID, leading to something like this:

[RAID5: 4 TB + 4 TB + [RAID5: 2 TB + 2 TB + 2TB]]  -> ??  -> ??

Should I keep the rest of the stack like it is, except change btrfs for ext4? Can btrfs handle the nestes RAID5 configuration, or does dmcrypt get in the way of that in any case?

---


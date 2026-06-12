---
title: "Adding additional RAID array disallows booting - Breezy Badger"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by chariscomp on 2007-04-10
Hello,

I have Ubuntu Breezy Badger installed on a computer and am using it as a server. I installed it onto a RAID 1 mirror using 2 SATA drives. I need to add more capacity to the server. So, I have purchased 2 PATA drives and went through the process of adding them as a RAID 1 mirror  as well. I was successful doing this all the way up to the point of rebooting the server after installing the PATA drives. Now, it evidently renumbers the md(x) drives. Originally, the SATA drives are mounted as /dev/md0 and /dev/md1 and the PATA drives are supposed to be /dev/md2. However, when booting, it is evidently renumbering these such that the PATA drives are /dev/md0 and the SATA drives are /dev/md1 and so on. I have tried every thing I could find including changing the mdadm.conf in /etc/mdadm/mdadm.conf to force the correct naming of these RAID arrays. Evidently, the kernel is numbering them before it ever reads mdadm.conf and is ignoring whatever I put in this. I am booting from the RAID array. Does anyone have any suggestions as to how I can add this additional storage capacity without this problem? Is there some kind of kernel parameter I can pass to the kernel during GRUB bootup? I am at my wit's end with this problem. The only solution I have come up with is to clone the SATA RAID array to the PATA RAID array and essentially switch their functions. I would really rather not do this! Any suggestions would be most appreciated. If this is in the wrong forum, please move it to the right forum. Thanks in advance for any help anyone can give.

Joshua Cook

---


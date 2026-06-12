---
title: "soft raid10 with mdadm with everything ONLY on raid"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by alkisx on 2009-02-25
I've seen many tutorials on how to create raid10 with mdadm. But no one with how to put everything (/boot and swap) on the raid created and partition it accordingly.

It seems like I am in an infinite loop trying to do that.

boot with the live cd, install mdadm, created the array of five disks, all great. I had an array on /dev/md0.

used cfdisk,fdisk or parted to partition it... great!

Every of the above utilities created the partitions md0p1, md0p2 and so on. With one exception. those device are nowhere on dev! Only visible on the partition programs. The only md device on /dev is the raid device md0 but not the partitions I created.

partprobe does nothing, as it says I have to reboot to reread the partition information. But how the hell I am supposed to do that if I have not even install anything? With the next reboot, of course once again from the live cd, I have to start all over (withoud recreated the partitions), nothing...

---

### Post by alkisx on 2009-02-26
Noone knows if it can be done?

---


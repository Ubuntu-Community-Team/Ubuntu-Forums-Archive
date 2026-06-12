---
title: "Upgrade to 9.10 on a Aspire One ZG5, how to improve Boot Time?"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by lingot on 2009-11-11
Hi,

My ZG5 had 9.04 installed as describe in the post:

[http://ubuntuforums.org/showthread.php?t=1270547](http://ubuntuforums.org/showthread.php?t=1270547)

I upgraded to 9.10 using the Update manager.

After reboot, I got the following error message:

One or more of the mounts listed in /etc/fstab cannot yet be mounted...

and boot time took over 2 minutes.

I believe it's because the filesystem of my /boot and root are ext2.

I couldn't find any data on the Web describing how to fix, therefore I decided to reinstall.

I decided to repartition, to have a /home partition, still using ext2 as filesystem but during the installation I keep getting the error message that it cannot mount one of the partition and fall back to the partition utility.

I end up having to use ext4 filesystem to have the install successful.

Unfortunately, I'm not sure that ext4 is the best fs for SSD.

But the main problem is that boot time is slow, very slow, close to 2 minutes, compare to 9.04 where I could boot and have Firefox loaded in 45 seconds.

Anyway to improve this?

Regards,

Lingot

---

### Post by lingot on 2009-11-11
I tried to set the elevator=noop and set to 0 in the fstab to prevent fsck. It didn't help much to improve boot time performance.

I check and apply the latest update, and now some of the default GNOME applet won't load properly, therefore removing quiet a lot of the usability.

If I can provide any more information to help debug these issue, please let me know.

Thanks

Lingot

---

### Post by lingot on 2009-11-15
Bug 432089 is discussing the issue, look they found a solution for slow HD, but not for SSD.

Hope it get fix in the future, for now I'm trying another distribution that boot in 15 seconds. ;-)

Cheers,

Huy

---


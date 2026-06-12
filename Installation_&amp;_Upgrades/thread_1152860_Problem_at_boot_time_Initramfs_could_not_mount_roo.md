---
title: "Problem at boot time Initramfs could not mount /root : device busy"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by athorretto on 2009-05-08
Hi all,

i'm encountering this problem so far from 8.10 and now ,also in 9.04, is presenting to me with a different error message but with the same result:

Grub is well configured for the 1° part ,the kernel is found and loaded ,the system show me the initramfs prompt saying that is unable to mount /root file system.

Now i've done much tests:

mount /root /dev/disks/by-uuid
also tried with by-label,by-id.. nothing ...

He says always device busy when i try to mount.

Is possible that there is an issue regarding an old Raid Striping Array that was on this disk (and another, also this connected into the machine)?  

Maybe my raid controller is not well managed by kernel?

Help me please to find out what is appening

---


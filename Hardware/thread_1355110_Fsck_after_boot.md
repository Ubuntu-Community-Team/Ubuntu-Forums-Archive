---
title: "Fsck after boot ?"
date: 2009-12-14
forum: Hardware
---

### Post by Raffles10 on 2009-12-14
I have a relatively new install of Ubuntu 9.10. I have two hard drives /dev/sda1 & /dev/sdb1 both ext3. Today for the first time a filesystem check was run on /dev/sdb1 but it ran after boot instead of before. I thought filesystem checks had to run in read only mode, before the filesystem was mounted.

In all previous Ubuntu versions fsck runs before boot and the system boots after it has completed. Is this a new method for fsck implemented in Karmic ?

[[img]http://omploader.org/tMnp0NQ[/img]](http://omploader.org/vMnp0NQ)

---

### Post by jocko on 2009-12-14
> **Raffles10 said:**
> I have a relatively new install of Ubuntu 9.10. I have two hard drives /dev/sda1 & /dev/sdb1 both ext3. Today for the first time a filesystem check was run on /dev/sdb1 but it ran after boot instead of before. I thought filesystem checks had to run in read only mode, before the filesystem was mounted.

In all previous Ubuntu versions fsck runs before boot and the system boots after it has completed. Is this a new method for fsck implemented in Karmic ?

[[IMG]http://omploader.org/tMnp0NQ[/IMG]]("http://omploader.org/vMnp0NQ")
When a filesystem that is not essential for booting needs to be checked it is checked silently in the background, and will get mounted when fsck is finished.
As you can see in your screenshot the mountall process is still running, waiting for fsck to finish.
There are some reported [bugs]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/439604") on this behaviour, where me and some others have been trying to get the developers to fix some kind of notification when this happens, as it otherwise may make you think you have lost a partition... But so far they don't seem to think that's very important...

---

### Post by Raffles10 on 2009-12-14
I agree some sort of notification is necessary. I had no idea whether this behaviour was normal for Karmic or some kind of error. In the past /dev/sdb1 was always checked prior to boot. If they're going to change the way fsck operates on non boot filesystems they should indicate it to the user somehow. :confused:

---


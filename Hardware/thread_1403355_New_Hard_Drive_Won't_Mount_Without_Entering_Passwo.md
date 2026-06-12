---
title: "New Hard Drive Won't Mount Without Entering Password.  Why?"
date: 2010-02-10
forum: Hardware
---

### Post by umechanism on 2010-02-10
I'm running Ubuntu 9.10 on a Dell Studio desktop.  The factory hard drive was getting full so I purchased a new 1TB Western Digital hard drive.  I formatted the drive NTFS.  I can read and write to the drive with no problem.  My issue is this - each time I start up the computer in the morning and click on "Places>1TB-Drive" I am prompted for my password before it can be mounted.  Why?  I just want the drive mounted automatically.

Here are my discs:
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1968    15728640    7  HPFS/NTFS
/dev/sda3   *        1968       46317   356239958+   7  HPFS/NTFS
/dev/sda4           46318       91201   360530730    5  Extended
/dev/sda5           46318       89971   350650723+  83  Linux
/dev/sda6           89972       91201     9879943+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c529c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

```


Here is my fstab:
```
#Mount 1-TB Drive
/dev/sdb /mnt/1TB-Drive ntfs-3g defaults,locale=en_US.UTF-8 0 0

```
How do I fix this where the drive is mounted automatically without prompting me for a password?

Thanks!

---

### Post by Morbius1 on 2010-02-10
I can see ntfs-config handiwork in that fstab entry ;)

Change this:
> [COLOR=Blue]/dev/sdb[/COLOR] /mnt/1TB-Drive ntfs-3g defaults,locale=en_US.UTF-8 0 0To this:
> [COLOR=Blue]/dev/sdb1[/COLOR] /mnt/1TB-Drive ntfs-3g defaults,locale=en_US.UTF-8 0 0

Now when you reboot it should mount automatically without prompting you for a password.

[I]BTW, it won't show up under "Places" any more because you set the mount point at "/mnt" instead of "/media" but you should have access to it at /mnt/1TB-Drive. Alternately , you could create a "bookmark" in nautilus to /mnt/1TB-Drive, then it will show up under Places in Nautilus.
[/I]

---

### Post by umechanism on 2010-02-10
Douhhhhh!
Dang it...I should have caught that.  Thanks.  I'll give it a try tonight.

---


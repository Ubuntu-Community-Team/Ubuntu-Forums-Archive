---
title: "Ubuntu not reding my HDD or External anymore?"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by SamTyson92 on 2007-12-13
I re-installed Windows XP recently and obviously it left Linux in tact but now I cannot resize or change any partitions using the partition editor and they wont show up on the desktop, really need to change the partion on my external drive ASAP but it won't let me it just has a warning sign next to it and the option of re-sizing is greyed out.

---

### Post by ajgreeny on 2007-12-13
Are they mounted, because you can't work on them if they are.  Try unmounting the partitions and then try again.  In ubuntu do ```
mount
``` and this will show you all mounted partitions, like this   

/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hda1 on /media/WindowsXP type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

Here, hda1 (at the bottom) is my windows partition and I can unmount it with ```
sudo umount /dev/hda1
```Give that a try.

---

### Post by SamTyson92 on 2007-12-15
Its not worked.
I've attached a screenshot of my problem, I have it with both my main internal HDD and external, I can still access them via Computer but it just won't let me resize them or edit them.

---


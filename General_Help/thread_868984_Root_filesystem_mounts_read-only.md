---
title: "Root filesystem mounts read-only"
date: 2008-07-24
forum: General Help
---

### Post by Xianath on 2008-07-24
After a power failure that got the best of the UPS, my Hardy server (running on a Dell Precision 690 FWIW) would no longer mount its root filesystem rw on boot. It wouldn't mount any other filesystems at all, either.

The curious part is:

```

/dev/sda1 on / type ext3 (rw)
...
/dev/sda4 on /var/lib/vmware/machines type jfs (rw,relatime,uid=1000,gid=1000)
/dev/sda4 on /var/lib/vmware/machines type jfs (rw,relatime,uid=1000,gid=1000)
/dev/sda4 on /var/lib/vmware/machines type jfs (rw)

```

Note how it *looks* mounted but neither is / write-enabled, nor is /var/lib/vmware/machines actually mounted despite there being three entries suggesting the opposite. df -h shows the following:

```

/dev/sda1             9.9G  6.6G  2.8G  71% /
...
/dev/sda4             9.9G  6.6G  2.8G  71% /var/lib/vmware/machines
/dev/sda4             9.9G  6.6G  2.8G  71% /var/lib/vmware/machines
/dev/sda4             9.9G  6.6G  2.8G  71% /var/lib/vmware/machines

```

Manually remounting / rw works, as does mounting any other filesystem. However this is just a temporary workaround that I can't use in production. I would like to find the root cause and fix this.

Here's what I've tried that hasn't helped:
1) e2fsck -f, came up clean
2) e2fsck -f -D (to force some changes), came up clean with changes
3) tune2fs -e continue, also changed fstab accordingly
4) changed fstab entries to device names rather than UUID

I'm at a loss as to what else to do. I've never in 12 years seen a filesystem being tainted like this. I'm open to any suggestions for things to try or other info to get.

Thanks,
Peter

---

### Post by VMC on 2008-07-24
I must be missing something here, because my root file system is mount read only. It's never been anything but read only.

Part of my fstab looks so:
# /dev/sda1
UUID=d8533154-cef1-4cce-a823-9f3f74aab65b /               ext3    relatime,errors=remount-[COLOR="Red"]ro[/COLOR] 0       1

---

### Post by chrisccoulson on 2008-07-24
VMC - "errors=remount-ro" actually defines the action to take if errors are found on the volume. In this case, the action is to remount the filesystem read-only. 

Xianath - Have you had a look in /var/log/syslog?

---

### Post by Xianath on 2008-07-24
Well... there's nothing in syslog because the filesystem was read-only when it happened :) I did catch a fleeting glimpse of "syslogd... something... read-only filesystem" before I got the login prompt. Before I go hunting for a serial cable, is there anything else I could try?

Cheers,
Peter

---

### Post by unutbu on 2008-07-24
Just out of curiosity, what is the output of 
```

dmesg
cat /etc/fstab
tune2fs -l /dev/sda1
```

---

### Post by Xianath on 2008-07-24
You're a genius! Not sure how I missed it before but it became fairly obvious once I put all these three together:

from dmesg:
```
[   47.153229] EXT3-fs: INFO: recovery required on readonly filesystem.
[   47.153232] EXT3-fs: write access will be enabled during recovery.
[   47.391990] EXT3-fs: sda1: orphan cleanup on readonly fs
[   47.391999] ext3_orphan_cleanup: deleting unreferenced inode 1081353
[   47.392671] ext3_orphan_cleanup: deleting unreferenced inode 1081352
[   47.392887] ext3_orphan_cleanup: deleting unreferenced inode 1081351
[   47.393063] EXT3-fs: sda1: 3 orphan inodes deleted
[   47.393064] EXT3-fs: recovery complete.
[COLOR="Red"][B][   47.394565] EXT3-fs: mounted filesystem with ordered data mode.
[   54.368303] EXT3-fs: cannot change data mode on remount[/B][/COLOR]
[   54.369490] EXT3-fs: cannot change data mode on remount

```

from fstab:
```
UUID=67b5ab01-ceeb-42f7-97e4-b4a0d3ea2a50 /               ext3    defaults,errors=continue,relatime,**[COLOR="Red"]data=writeback[/COLOR]** 0       1
```

from dumpe2fs:
```
Default mount options:    **[COLOR="Red"](none)[/COLOR]**
```

So it was trying to mount / rw but failed to do so because the default mount option would be data=ordered and you can't change that with a remount. So, I removed that from fstab and set it with tune2fs. All set.

Thanks for your help!

Peter

P.S. I still don't know where the errors come from when the filesystem is reported clean by tune2fs and e2fsck. Not sure I want to lose sleep over it though.

---


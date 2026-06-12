---
title: "new install won't boot"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by sugargenius on 2008-12-11
Installed 8.10 server on new box with 5 drives.  4 are SATA, 1 is PATA.  In setup, they all showed up as /dev/sd?...even the PATA drive...

The PATA drive was to be os/system.  The other 4 i was going use for lvm

After I installed, I rebooted and all I see at botton is 
GRUB

I let it sit there for a few minutes, but nothing happened.

I look in bios at hd boot boot priority, and moved the PATA to the top of the list.

Reboot

Nothing.  Not even GRUB

Re-install

Reboot

Nothing.

I don't really want to spend much time trying to 'fix' what I've done.  I'd really like to just start over clean...no GRUB, no partitions, no LVM.  Is there an easy way to do that?

Here's output from fdisk:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1500.3 GB, 1500300828160 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930275055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a380a3b

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a380a3a

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a380a39

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a380a38

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00095b3c

   Device Boot      Start         End      Blocks   Id  System

```

reinstalled again and it booted this time.  However, now it thinks the "os" drive is /dev/sdb...just a minute ago it was /dev/sde
```

Disk /dev/sda: 1500.3 GB, 1500300828160 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930275055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a380a3b

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00095b3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   374796449   187398193+  83  Linux
/dev/sdb2       374796450   390716864     7960207+   5  Extended
/dev/sdb5       374796513   390716864     7960176   82  Linux swap / Solaris

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a380a3a

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a380a39

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a380a38

   Device Boot      Start         End      Blocks   Id  System

```

Is it going to remap os drive to a different /dev/sd? every time I re-boot?  So far, FDISK has reported it as:
/dev/sdb
/dev/sdc
/dev/sde

I did re-order the hd boot priority...once, but even grantin that change would change the /dev/sd?...I should have only 2 different device mappings for that drive...not 3

What gives?

---


---
title: "Can I recover this system?"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by valkyrie on 2009-10-05
I have had Windows Vista and Ubuntu cheerfully running on the same laptop for months. Today, I was booting, and ended up hitting something besides "enter" in Grub -- I think it ended up going into Vista recovery, and the next thing I know it gives me a Windows background, and then (in big red letters) "ERROR".

Upon reboot, grub didn't give a list of boot options, it gave Error 22. However, the process described in [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) for restoring grub isn't working; "find /boot/grub/stage1" just returns an error, regardless of which /dev/sda# is mounted. I also walked through [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub) to find out which sda# exactly I should be working with, and can't find any linux-like files on any of the partitions.

Currently, fdisk -l returns the following:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12289693+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1531       14555   104616444    7  HPFS/NTFS
/dev/sda3           14556       38913   195655635    f  W95 Ext'd (LBA)
/dev/sda5           20987       38913   143998596    7  HPFS/NTFS

```

I am worried that whatever restore-Vista-process I accidentally started has simply wiped the Linux partitions; however, it wasn't running very long (a few minutes, not nearly enough time to format 160+ GB) and so I am hopeful that it's a matter of restoring partitions instead. However, I don't really want to play in the partitioner in case I accidentally end up formatting the former Linux partition -- I could really, really use some data that is (was?) on there.

Your advice is appreciated :)

---

### Post by earthpigg on 2009-10-05
hi,

before attempting to restore partitions and whatnot, you should first recover whatever vital data you had that was not backed up using testdisk.

from the live cd:
```
sudo apt-get install testdisk
```

then peruse the photorec and testdisk wikis: 

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

once you are ready, go ahead and use photorec to recover your vital stuff (dont let the name fool you, photorec isn't just for pictures...):

```
sudo photorec
```


as for windows and ubuntu fighting over your MBR, im afraid i cannot be of help as i don't use windows.

---

### Post by valkyrie on 2009-10-06
My main priority *is* getting the data. If I can do that (and certainly looks like I can, thank you for that!), then I can go ahead and reinstall Ubuntu after that. Thank you!!!

---


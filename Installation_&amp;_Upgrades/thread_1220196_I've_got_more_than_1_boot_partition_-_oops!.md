---
title: "I've got more than 1 boot partition - oops!"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2009-07-22
In the process of trying to fix/reinstall a corrupted Ubuntu 8.04.3 system I managed to mess up in the partioning part of the alternate cd.  I have a dual boot system with Windows on one drive and Ubuntu on the second.  On the Ubuntu drive I have a separate home partition.

Now I have two bootable partitions, one on the Windows drive where I want it, and the other is the / partition on the Ubuntu drive.  Here is the result of fdisk -l:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091d63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974       24321   187542810    5  Extended
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris
/dev/sda6           23161       24133     7815591    b  W95 FAT32
/dev/sda7             974       23159   178208982   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x703e7a4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         914     7341673+   7  HPFS/NTFS
/dev/sdb2             915        7475    52701232+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

sda1 is the Ubuntu drive which should not be bootable, and sdb1 is the Windows drive which should be bootable.  It looks like I have messed up my Grub.  Now I am leary of going in there and making it worse.  At the moment I do not have access to either Ubuntu or Windows so everything will have to be done via the live cd.

Can anyone help me out with step-by-step instructions so I can recover my system?  Thanks

---

### Post by ajgreeny on 2009-07-22
Try the [**supergrub**]("http://www.supergrubdisk.org/") disk.  With this you can reset the windows MBR, just for starters, then you can reinstall grub again.

---

### Post by Baasha on 2009-07-22
Ok, I have the SuperGrubDisk, but still having a problem.

Part of the corruption on my system is that the screens when booting up and also the screens in the SGD are way off to the left.  I have my monitor horizontal position set as far to the right as possible, but I still can't read enough to be sure of what I am doing.  The weird thing is that screens produced from the Ubuntu live cd are centered normally.  I can't figure out how to correct this -- there don't seem to be any settings in the bios that would control font size or screen position.  After booting into an OS these things would be controlled from whatever is running (AFAIK).

Any ideas about how to fix this?  If I can get past this little roadblock then maybe I can figure out how to use SGD to remove the boot sector from one of my drives.  Thanks.

---

### Post by starcannon on 2009-07-22
You can just use the ubuntu live CD to solve this little matter:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

This link is for a different problem, but the same solution.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That should do it; just be sure to put grub where you want it, then just ignore the other boot partition, its such a small amount of space that I wouldn't spend to much time worrying about it (perhaps when you upgrade ubuntu you can absorb it into /root).

GL and HF

---


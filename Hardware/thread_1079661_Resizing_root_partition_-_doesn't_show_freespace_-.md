---
title: "Resizing root partition - doesn't show freespace - gParted"
date: 2009-02-24
forum: Hardware
---

### Post by banjo man on 2009-02-24
so, I decided to dump one of my winxp installs and use the space for ubuntu (root).
I booted the livecd (this is 8.10 I'm talking about, by the way) and started gparted. went through all the prompts for resizing, and came up with an error:

> See the details for more information.

IMPORTANT
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information.

so I saved it, and will attach to end..

it also said something about the kernel not recognizing the new partition or something like that (until reboot).

so, I rebooted and everything started fine, but when I check the freespace it still says there is the same amount as before (the total size shown is correct, but the free space doesn't show)

I've tried fsck as suggested from livecd, but it doesn't seem to help

---

### Post by taurus on 2009-02-24
Do you want to expand /dev/sda1 to take up that unallocated space?  From the LiveCD, post the output of this command.

```
sudo fdisk -lu
```

---

### Post by banjo man on 2009-02-24
here it is

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   245762369   122881153+  83  Linux
/dev/sda2       344549375   405985279    30717952+   f  W95 Ext'd (LBA)
/dev/sda3   *   405987240   467427239    30720000    7  HPFS/NTFS
/dev/sda4       467427240   488392064    10482412+  de  Dell Utility
/dev/sda5       344549376   405985279    30717952    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0942df08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   234452609   117225281    7  HPFS/NTFS

Disk /dev/sdd: 2031 MB, 2031091712 bytes
16 heads, 32 sectors/track, 7748 cylinders, total 3966976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        8064     3966975     1979456    b  W95 FAT32
ubuntu@ubuntu:~$ 



I originally had ext3 ubuntu ~30gb, and an ntfs part ~150-ish (it's been awhile since I removed the partition, just now need some space) I think I'll just expand sda1 the full amount instead of trying to set another small win-games partition

---

### Post by Panzor on 2009-02-25
If I'm understand correctly, then you want your HDD to be completely ubuntu. The way I would do this to save time would be to back up my /home directory and a few files like /etc/fstab and do a full reinstall, then overwrite the home directory, fix the owners (chown), and you're on your way. Actually, if it was me, I'd boot an alternate install cd and encrypt it all. Good luck, and sorry if I totally missed the point :P.

Also, doing this will save all of your settings for (nearly, but I can't think of an exception) all your apps...but they won't be installed yet. Once they are installed, they automagically have all your old settings. Linux ftw. *salutes*

---

### Post by banjo man on 2009-02-26
I would (and almost might) just do that, but I also have a win7 install that I'm using...

I could do with a new install (might try jaunty build ;)

I was just hoping to not have to reinstall just to get some free space, and it looks like it worked, but there's some problem with a way the space is added that doesn't give me access or something....(I'm not up on disc managment as much as networking, etc...)


thanks for the help

---


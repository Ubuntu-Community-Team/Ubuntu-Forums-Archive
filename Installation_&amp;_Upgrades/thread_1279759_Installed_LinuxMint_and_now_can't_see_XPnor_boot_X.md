---
title: "Installed LinuxMint and now can't see XP/nor boot XP"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by Shadowking on 2009-10-01
Hi all,

I installed Linux Mint on my dad's pc. But something must have screwed up. I think I messed up grub. 
Now I can't access the windows XP files. Plus I can't even see those files in Linux. This is the fdisk-l.

[COLOR=Red]
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1ddb1dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        9963    54428220    f  W95 Ext'd (LBA)
/dev/sda5            3188        5737    20482843+   b  W95 FAT32
/dev/sda6            5738        8287    20482843+   7  HPFS/NTFS
/dev/sda7            8288        9963    13462438+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcb0dcb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5977    48010221    7  HPFS/NTFS
/dev/sdb2            5978       30401   196185780    f  W95 Ext'd (LBA)
/dev/sdb5            5978       11076    40957686    7  HPFS/NTFS
/dev/sdb6           11077       17991    55544706    7  HPFS/NTFS
/dev/sdb7           17992       30030    96703236   83  Linux
/dev/sdb8           30031       30401     2980026   82  Linux swap / Solaris[/COLOR]

This is the menu.lst file for grub. (I've included only the essential part)

[COLOR=Red]title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb7 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb7 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria, memtest86+
root        (hd0,6)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
grub> map (hd0) (hd1)
grub> map (hd1) (hd0)
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
[/COLOR]
[COLOR=Black]Really need to recover those files and get xp back online for my dad. Any help is appreciated. 

Thanks
[/COLOR]

---

### Post by Mark Phelps on 2009-10-01
Presuming you're booting from the disk containing Mint, your setup files look OK.

Are you sure the XP files are gone? The partitions appear to be still there.

Have you gone into Places and tried opening any of the folders there to confirm that they are empty?

---

### Post by presence1960 on 2009-10-01
Let's get a better look at your setup & boot process. Boot into Ubuntu (Mint). Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text

---


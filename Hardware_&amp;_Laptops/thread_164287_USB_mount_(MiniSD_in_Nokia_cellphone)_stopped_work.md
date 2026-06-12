---
title: "USB mount (MiniSD in Nokia cellphone) stopped working"
date: 2006-04-22
forum: Hardware &amp; Laptops
---

### Post by knubbe on 2006-04-22
Hi.
I used to mount my cellphone's MiniSD card simply by connecting the USB cable between the phone and my laptop. Worked like a charm actually. However, it was some weeks ago the last time i did it and ive downloaded a couple of updates since. 

Now when i connect my phone i get:

"Could not mount unit:
Error reported:
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab"

So i tried to manually mount it:
sudo mount /dev/sdc /media/sdc
mount: /dev/sdc: can't read superblock

my dmesg | tail:
[4316550.922000] NTFS-fs error (device sdc): ntfs_fill_super(): Device has unsupported hardsect_size.
[4316550.968000] HFS+-fs: unable to find HFS+ superblock
[4316551.012000] VFS: Can't find a HFS filesystem on dev sdc.
[4316551.051000] VFS: Can't find ext3 filesystem on dev sdc.
[4316551.089000] VFS: Can't find an ext2 filesystem on dev sdc.
[4316551.133000] ReiserFS: sdc: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdc
[4316551.177000] XFS: bad magic number
[4316551.177000] XFS: SB validate failed
[4316576.419000] FAT: logical sector size too small for device (logical sector size = 512)
[4316580.609000] FAT: logical sector size too small for device (logical sector size = 512)

As you can see i've tried several different filetypes but when it all ends up, it always say: cant read superblock.

sudo fdisk -l:
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        1027     8161020    7  HPFS/NTFS
/dev/sda3            6904        7295     3148740   db  CP/M / CTOS / ...
/dev/sda4            1028        6903    47198970    5  Extended
/dev/sda5   *        1028        6718    45712926   83  Linux
/dev/sda6            6719        6903     1485981   82  Linux swap / Solaris

Partition table entries are not in disk order
Note: sector size is 1024 (not 512)

Disk /dev/sdc: 2032 MB, 2032665600 bytes
63 heads, 62 sectors/track, 508 cylinders
Units = cylinders of 3906 * 1024 = 3999744 bytes

   Device Boot      Start         End      Blocks   Id  System




Im a bit confused since this used to work. Anyone who can help me out?

---

### Post by DaveQB on 2006-12-24
Exact same problem here.  My issue is going from a 512MB MiniSD card to a new Transcend 2GB MiniSD card for my Nokia 6280.

Kubuntu Dapper here.

Any idea's ?

---

### Post by sebos69 on 2007-01-03
it might be related to this prolem (which I experience also...)


[http://bugzilla.kernel.org/show_bug.cgi?id=7201](http://bugzilla.kernel.org/show_bug.cgi?id=7201)

---

### Post by Noky on 2007-01-04
Not the excat same problem. I just tried hooking up my E62. First time I used PC Suite which didn't seem to do anything. I then tried Data Transfer and the OS crash/froze instantly (music stopped, mouse frozen, no response from pushing power button, had to reset). I'm sure I can do it again, don't know how to report any info though.

---

### Post by DaveQB on 2007-01-04
It seems my phone [Nokia 6280] doesn't work in Data Storage mode with a 2GB card in it, even in Windows.  At least that's what my googling found.

---

### Post by Noky on 2007-03-01
I don't know if anyone has realized but my Nokia E62 no longer freezes up when I plug it in under data storage mode. I believe if I don't eject after writing data it will lock up but I'm not sure (I don't remember correctly). In short, my phones doesn't work in PC Suite mode (no syncing :( ) but I can send data to it.

---


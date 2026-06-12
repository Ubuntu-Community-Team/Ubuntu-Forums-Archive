---
title: "Trouble mounting external hard drive"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by dhigger on 2007-03-15
I am having trouble mounting a (possibly faulty) external (USB) HDD. I am running Ubuntu Edgy (kernel 2.6.17-11-generic). It is not automatically mounted when I plug it in, whereas another drive I have *is* automatically mounted without a problem. I really want to recover the data on the problem disk!

Here is the output of [FONT="Courier New"]fdisk -l[/FONT]:

[FONT="Courier New"]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS[/FONT]

The 80GB /dev/sda is the problem disk. It seems to be a FAT32 filesystem type.
Trying [FONT="Courier New"]mount -t vfat /dev/sda /mnt/usb[/FONT] produces this:

[FONT="Courier New"]mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/FONT]

...and [FONT="Courier New"]dmesg | tail[/FONT] then gives

[FONT="Courier New"][17217170.160000]     Additional sense: Unrecovered read error
[17217170.160000] end_request: I/O error, dev sda, sector 56
[17217170.160000] Buffer I/O error on device sda, logical block 7
[17217220.812000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17217220.812000] sda: Current: sense key: Medium Error
[17217220.812000]     Additional sense: Unrecovered read error
[17217220.812000] end_request: I/O error, dev sda, sector 64
[17217220.812000] Buffer I/O error on device sda, logical block 8
[17217240.704000] FAT: invalid media value (0x00)
[17217240.704000] VFS: Can't find a valid FAT filesystem on dev sda.[/FONT]

How can I get the data off? I have started [reading]("http://linuxgazette.net/issue32/tag_superblock.html") about commands such as [FONT="Courier New"]dd[/FONT] and [FONT="Courier New"]buffer[/FONT]. Are these what I need?

TIA

---

### Post by dhigger on 2007-03-15
Well, I've continued looking around and have come across [GNU ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html"). Why ddrescue is better than dd, dd_rescue or dd_rhelp is explained [here]("http://www.toad.com/gnu/sysadmin/index.html#ddrescue"), if you'd like that info.

Here is [ help on using dd_rescue]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html").

I also had to [enable NTFS-write capability]("http://ubuntuforums.org/showthread.php?t=217009"). (I needed this because I wanted to copy data from the bad external HDD to the good external HDD as seen in my previous post. The good drive is an NTFS filesystem, so to use it I needed linux to write to NTFS.)

Using [FONT="Courier New"]df -k[/FONT] I found out where my good drive lived (the path to it).

[FONT="Courier New"]sudo ddrescue /dev/sda /media/BackUp/backup.img[/FONT]
...and dd_rescue is chuntering away at 22GB and counting....I'll let you know how it goes....

Dave

---

### Post by dhigger on 2007-03-15
dd_rescue did it's thing and finished successfully writing a .img file to my NTFS external hard drive.

I am now having problems mounting the IMG, to browse / copy files out from it.

I have created a mount point, then used the [FONT="Courier New"]-o loop[/FONT] trick, and still [FONT="Courier New"]mount[/FONT] complains that I need to specify the filesystem type. Whatever I try (ntfs (which should be correct I think), hpfs, vfat), nothing works. The output of [FONT="Courier New"]dmesg | tail[/FONT] always has errors saying that no filesystem of that type was found.

Any ideas?! How can I get my files out of that .img file, which is on my NTFS HDD?

Help!

Edit: here's what I've been trying: [FONT="Courier New"]sudo mount -o loop backup.img /mnt/recoverydata -t ntfs[/FONT]
and [FONT="Courier New"]sudo mount -o loop backup.img /mnt/recoverydata -t auto[/FONT]

---


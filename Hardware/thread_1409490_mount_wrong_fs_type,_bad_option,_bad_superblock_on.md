---
title: "mount: wrong fs type, bad option, bad superblock on /dev/sdd1"
date: 2010-02-17
forum: Hardware
---

### Post by IAmNotAUser on 2010-02-17
I'm running on an Asus EEE and recently bought a 16Gb SDHC card off eBay.

I'm trying to copy a collection of video files onto it, however the files error about 3/4 of the way through the transfer claiming the filesystem is suddenly readonly.

The original filesystem was FAT32, so I tried using my Windows machine to format it back to a clean FAT32 fs and tried again, with the same result. I then tried doing the transfer from the Windows machine, and got a strange error code.

Since then, I've used  gparted to format the card to NTFS and ext3 and 4. After that, when I try to open them on my EEE they return the "mount: wrong fs type, bad option, bad superblock on /dev/sdd1" message. I tried doing dmesg | tail as it suggests and get:

```
doug@doug-eee:~$ dmesg | tail
[  838.652224]  sdd: sdd1
[  838.654240] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[  852.158316] JBD: no valid journal superblock found
[  852.158325] EXT3-fs: error loading journal.
[  866.494868] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 955
[  986.494221] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 863
[ 1106.493537] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 837
[ 1118.176677] JBD: no valid journal superblock found
[ 1118.176690] EXT3-fs: error loading journal.
[ 1129.613375] usb 1-2: USB disconnect, address 2
```I have tried checking the filesystem in both Win and Ubuntu. In Windows and formatted to FAT32 the drive reports no errors, and in Ubuntu (the last fs I formatted to was ext3) I get the result:

```
doug@doug-eee:~$ sudo fsck.ext3 /dev/sdd1
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: No such file or directory while trying to open /dev/sdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

```Any ideas what I can try now? Is there a way I can determine if the card is faulty or not? Or is this some issue with cards and I'm going to have to look into getting a similar sized USB?

Thanks.

---

### Post by dabl on 2010-02-17
You may have just discovered _why_ it was for sale on E-Bay. :cry:

I've got several 4GB, 8GB, and one 16GB SDHC cards.  I can tell you they don't last forever.

Probably it is worth one try of "dd".  From your Linux system, with the card inserted, run ```
sudo fdisk -lu
``` and be sure of the card's /dev/sdx number.  You don't want to make a mistake on this!  Now

```
sudo dd if=/dev/zero of=/dev/sd_x_ bs=512 count=1
```

where "x" is the number that you learned from fdisk.

When the process completes, run GParted again.  Choose "MS-DOS" for the partition table type, and choose ext2 for the filesystem type.

If it works this time --- great.  If not, you've got a piece of dumpster food (or "dustbin" food for UK folks).

---

### Post by IAmNotAUser on 2010-02-17
Thanks so much for your quick reply.

After doing the dd, setting the partition table to msdos and filesystem type to ext2 I'm now able to mount the card, which is a start...I'll start the transfer now, and  see how things stand in an hour before I consider the dustbin ;) (yes I'm a Brit :P )

---

### Post by dabl on 2010-02-17
Good.  ext2 is, of course, a Linux filesystem that will not be recognizable to Windows.  But, this is a Linux forum, so ....

:D

---


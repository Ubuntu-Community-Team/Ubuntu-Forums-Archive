---
title: "Unable to open fat32 partition"
date: 2016-05-26
forum: Hardware
---

### Post by letelu369 on 2016-05-26
Hi
I have a problem with my secondary HD, at the boot the system do  not start, I have removed the HD and connect it at the pc with an  usb-sata+ide adapter.
This is the output of fdisk -l of this device


/dev/sdc1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdc2          206848   210146264   104969708+   7  HPFS/NTFS/exFAT
/dev/sdc3       210146326   976773167   383313421    f  W95 Esteso (LBA)
/dev/sdc5       210146328   425577914   107715793+  83  Linux
/dev/sdc6       425577978   430734779     2578401   82  Linux swap / Solaris
/dev/sdc7       430734843   691598249   130431703+   7  HPFS/NTFS/exFAT
/dev/sdc8       691598313   893519234   100960461    b  W95 FAT32
/dev/sdc9       893519298   976773167    41626935   83  Linux

the partitions are all read and it's possible mount it, but not the sdc8. This partition have an FAT32 filesystem.
I have attemp to found information with
blkid, the UUID of the sdc8 partition are not displayd, the other yes.


dmesg | tail
[ 1456.821190] EXT4-fs (sdc8): VFS: Can't find ext4 filesystem
[ 1456.827662] EXT4-fs (sdc8): VFS: Can't find ext4 filesystem
[ 1456.827977] EXT4-fs (sdc8): VFS: Can't find ext4 filesystem
[ 1460.371911] sd 5:0:0:0: [sdc] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1460.371916] sd 5:0:0:0: [sdc] Sense Key : Medium Error [current]
[ 1460.371918] sd 5:0:0:0: [sdc] Add. Sense: Unrecovered read error
[ 1460.371919] sd 5:0:0:0: [sdc] CDB:
[ 1460.371920] Read(10): 28 00 29 38 f3 ea 00 00 01 00
[ 1460.371927] blk_update_request: critical medium error, dev sdc, sector 691598314
[ 1460.371952] FAT-fs (sdc8): bread failed, FSINFO block (sector = 1)

dumpe2fs /dev/sdc8 | less
dumpe2fs 1.42.9 (4-Feb-2014)
dumpe2fs: Attempt to read block from filesystem resulted in short read while opening /dev/sdc8
Could not find a valid superblock for filesystem.


fsck /dev/sdc8
fsck da util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
fsck.ext2: Attempt to read block from filesystem resulted in short read while opening /dev/sdc8
It 'possible that this is a zero-width partition?


This are all the information what I have found. There is the possibility to save data?
Thanks

---

### Post by oldfred on 2016-05-26
The e2fsck is for the ext family of formats.

You need chkdsk from Windows or Linux tools for vfat.

 sudo fsck.vfat -t -a /dev/sdc8 
or
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sdc8
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---


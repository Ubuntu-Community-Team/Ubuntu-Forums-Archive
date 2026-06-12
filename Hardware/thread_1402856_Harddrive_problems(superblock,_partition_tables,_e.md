---
title: "Harddrive problems(superblock, partition tables, etc) - need urgent help"
date: 2010-02-09
forum: Hardware
---

### Post by zuperxtreme on 2010-02-09
So it seems everything broke at once. I can't boot at all and it seems I can't mount.

I try: > ubuntu@ubuntu:~$** sudo fdisk -l**

Disk /dev/sdb: 8032 MB, 8032092160 bytes
5 heads, 32 sectors/track, 98048 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              51       98048     7839808    c  W95 FAT32 (LBA)


Which is only the Pendrive I have connected.

This doesn't work either:
> ubuntu@ubuntu:~$ **sudo fsck /dev/sda1**
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 


Nor does **sudo fsck /dev/sda2**. I try **sudo fsck /dev/sda** and I get:

> ubuntu@ubuntu:~$ **sudo fsck /dev/sda**
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?


But I suppose that's because it's the whole harddrive.

I try: > ubuntu@ubuntu:~$** sudo blkid**
/dev/loop0: TYPE="squashfs" 
/dev/sda5: TYPE="swap" UUID="97a71c98-45c8-4437-8a03-9238252d59d9" 
/dev/sdb1: LABEL="INTERNETZ" UUID="CE39-5A71" TYPE="vfat" 
ubuntu@ubuntu:~$ 


and neither /dev/sda, /dev/sda1 or /dev/sda2 is listed.

When I try to mount it from the "Places" menu(it shows both my partitions, but can't mount them), I get:

**"mount: wrong fs type, bad option, bad superblock on/dev/sda1, missing codepage or helper program or other error. In some cases useful info is found in syslog - try dmesg|tail or so"**

I can't get anything out of syslog and dmesg gives me:

> ubuntu@ubuntu:~$** dmesg|tail**
[ 3708.231634] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 3708.231639] end_request: I/O error, dev sda, sector 167750793
[ 3708.231667] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 3708.231671] end_request: I/O error, dev sda, sector 167750793
[ 3708.231696] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 3708.231700] end_request: I/O error, dev sda, sector 167751321
[ 3708.231718] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 3708.231722] end_request: I/O error, dev sda, sector 167751321
[ 3708.231742] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 3708.231746] end_request: I/O error, dev sda, sector 167751321
ubuntu@ubuntu:~$ 


I looked up what a bad superblock was and I tried doing:

> ubuntu@ubuntu:~$** sudo e2fsck -b 8139 /dev/sda1**
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 


This all started before yesterday, after a hard reset because the PC froze. Then it did a file system check and found a bunch of bad clusters. I agreed to everything and now I'm here. I probably erased important stuff...

At this point I don't care about the data any more, I just need to get this hard drive fixed. Any help would be appreciated, on top of it all it's a PC at work. So I'll have to work from the live-CD for now. :p

HALP =[

---

### Post by zuperxtreme on 2010-02-09
Hmm. Looks like it's hardware related. I changed around the SATA cables and conections and now I see the hard drives fine. You can close this thread if you'd like, mods.

---


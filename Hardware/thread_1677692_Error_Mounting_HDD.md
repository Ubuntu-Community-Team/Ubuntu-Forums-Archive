---
title: "Error Mounting HDD"
date: 2011-01-29
forum: Hardware
---

### Post by toemos on 2011-01-29
Hi there,

Iv have just moved overseas and brought all my old HDDs from home and put them in a new PC. They are all working perfectly apart from one which is failing to mount on Ubuntu. 

The error I receive is as follows.

Unable to mount Media

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so

and dmesg | tail outputs this -

```
tom@Roach:~$ dmesg | tail
[  203.989641] EXT3-fs (sda1): using internal journal
[  203.989645] EXT3-fs (sda1): mounted filesystem with ordered data mode
[  206.432786] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 768 not in group (block 1793450583)!
[  206.433050] EXT3-fs (sdb1): error: group descriptors corrupted
[  560.941805] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 768 not in group (block 1793450583)!
[  560.942057] EXT3-fs (sdb1): error: group descriptors corrupted
[  617.751340] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 768 not in group (block 1793450583)!
[  617.751602] EXT3-fs (sdb1): error: group descriptors corrupted
[  650.823553] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 768 not in group (block 1793450583)!
[  650.823814] EXT3-fs (sdb1): error: group descriptors corrupted
```

I have had a quick search around the forums and tried one or two suggestions without avail.

I would really like to recover the data on the hard drive, if possible :-?, so any help would be GREATLY appreciated.

Thanks, Tom.

PS on a side note I can access this hard drive on XP Pro using an ext driver, but the whole system crashes if I try to copy/open the files.

---

### Post by IcarusR on 2011-01-29
Try running fsck on the drive.

---

### Post by toemos on 2011-01-31
unfortunatley fsck doesnt fix the problem. it out puts errors as follows

```
tom@Roach:~$ sudo fsck /dev/sdc
[sudo] password for tom: 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

tom@Roach:~$ sudo e2fsck -b 8193 /dev/sdc
e2fsck 1.41.12 (17-May-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I dont understand much about blocks and superblocks, so I am a bit lost with this :S

---

### Post by toemos on 2011-01-31
I just noticed while reading over the errors that it was running fsck.ext2.
I tried changing it to ext3 and still got errors.

```
tom@Roach:~$ sudo fsck -t ext3 /dev/sdc1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext3: Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block when using the backup blocks
fsck.ext3: going back to original superblock
fsck.ext3: Device or resource busy while trying to open /dev/sdc1
Filesystem mounted or opened exclusively by another program?

```

---

### Post by xovertheyearsx on 2012-06-13
> **IcarusR said:**
> Try running fsck on the drive.

thanks [IcarusR]("http://ubuntuforums.org/member.php?u=179763") becuase without this command, i would have pulled my hair out! i ran in to the initramfs issue ([SIZE=1][Disk by UUID not detected  (initramfs), boot failure]("http://askubuntu.com/questions/15515/disk-by-uuid-not-detected-initramfs-boot-failure")[SIZE=2])[/SIZE] [/SIZE][SIZE=2]and ran a MBR repair which screwed up GRUB inadvertently. 

By this point my laptop thought I had no OS and I've been running off a live medium trying to access my HDD and all 250gb of it's contents!!! :cry:

But then I found this post since I was having a hard time mounting the filesystem and ran the command and it instantaneously worked! :guitar:

so a big thank you for this reply since it saved my @55!
 [/SIZE]

---

### Post by Implactus on 2012-08-06
I was having a similar issue with a sd card it wouldn't mount and kept giving errors as described above.:(
I opened the disk management utility and checked the file system which reported back after about 30 seconds that the file system was fine.:confused:
I then re-formatted the drive using the Fat file system which the notes said would make it compatible with all types of system.:popcorn:
Once formatted I tried the mounting the  drive from the disk management utility and it all came to life!:guitar::guitar:

---


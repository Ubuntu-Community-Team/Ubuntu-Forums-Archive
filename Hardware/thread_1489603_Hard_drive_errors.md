---
title: "Hard drive errors"
date: 2010-05-21
forum: Hardware
---

### Post by boralyl on 2010-05-21
As of yesterday I started having problems with my secondary internal hard drive.  It's only used as storage space, so there is nothing super important on it, but I'd still like to try to fix it.

As of yesterday it started saying it was in read-only mode even though it's mounted as readable and writable.  Doing a directory listing was on the hard drive was given weird output with question marks.  I unmounted it, and ran```

sudo e2fsck -f -y -b 32768 /dev/sdb1

```

It outputted a lot of information about fixing issues.  Today now it is still giving me problems.  I rebooted and it won't even mount it anymore.  Here is some output when trying a few commands:

```

spandan@htpc:~$ sudo e2fsck -c /dev/sdb1
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
spandan@htpc:~$ sudo mke2fs -n /dev/sdb1
mke2fs 1.41.9 (22-Aug-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
24420352 inodes, 97677200 blocks
4883860 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
2981 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968

spandan@htpc:~$ sudo e2fsck -f -y -b 32768 /dev/sdb1
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
spandan@htpc:~$ sudo fdisk -l /dev/sdb1
spandan@htpc:~$
spandan@htpc:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

spandan@htpc:~$ dmesg | tail
[  632.448007] Buffer I/O error on device sdb, logical block 0
[  632.448015] Buffer I/O error on device sdb, logical block 1
[  632.448020] Buffer I/O error on device sdb, logical block 2
[  632.448050] sd 3:0:0:0: [sdb] Unhandled error code
[  632.448054] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  632.448060] end_request: I/O error, dev sdb, sector 0
[  698.348128] sd 3:0:0:0: [sdb] Unhandled error code
[  698.348136] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  698.348144] end_request: I/O error, dev sdb, sector 65
[  698.348175] EXT3-fs: unable to read superblock

```

Line relevant in My /etc/fstab:
```
/dev/sdb1       /mnt/drive2     ext3    defaults        1       2
```

Any ideas on what I can do to fix this drive?

Thanks in advance.

---


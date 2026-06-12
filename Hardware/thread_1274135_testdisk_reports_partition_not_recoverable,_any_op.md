---
title: "testdisk reports partition not recoverable, any options?"
date: 2009-09-24
forum: Hardware
---

### Post by veggiefish on 2009-09-24
Hi,

I got the "target filesystem doesnt have /sbin/init" error at bootup.

So I followed instructions on various threads [http://ubuntuforums.org/showthread.php?t=1167710](http://ubuntuforums.org/showthread.php?t=1167710)

I booted into a live CD and attempted to mount my / filesystem, as you can see from the dmesg output, this failed trying with ext2, ext3 and cifs:

```

ubuntu@ubuntu:/dev$ sudo mount -t cifs /dev/sdb2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/dev$ dmesg | tail
[ 1674.273677] EXT2-fs: unable to read superblock
[ 2197.428874] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2197.428877] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 2197.429053] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2207.824055] eth0: no IPv6 routers present
[ 2471.896139] 0000:00:19.0: eth0: Link is Down
[ 2810.688289] attempt to access beyond end of device
[ 2810.688292] sdb2: rw=0, want=4, limit=2
[ 2810.688295] EXT3-fs: unable to read superblock
[ 2880.352200]  CIFS VFS: cifs_mount failed w/return code = -22

```So I ran testdisk:

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 250 GB / 232 GiB - CHS 30395 255 63

The harddisk (250 GB / 232 GiB) seems too small! (< 353 GB / 328 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                14802   0  1 42937 252 61  452004712


[ Continue ]

EXT3 Large file Sparse superblock Recover, 231 GB / 215 GiB

```Is there anything I can do to recover this drive, I am already running testidsk again, but I dont want to lose data. Thanks in advance!

---

### Post by veggiefish on 2009-09-24
I also tried fsck, 

```

ubuntu@ubuntu:~$ sudo e2fsck -f -D /dev/sdb
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ e3fsck -f -D /dev/sdb
bash: e3fsck: command not found
ubuntu@ubuntu:~$ e2fsck -f -D /dev/sdb2
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Permission denied while trying to open /dev/sdb2
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ sudo e2fsck -f -D /dev/sdb2
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?

```

---


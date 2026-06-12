---
title: "Ext3 partition not mounting"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by Rikva on 2005-11-14
Last week I had not enough space in my homedirectory, so I decided to partition my second drive . I made a new linux (83) partition with cfdisk and made it ext3 using "mke2fs -j /dev/hdb2".
I mounted the partition and moved 50gb from my homedirectory to the fresh partition.
Yesterday I came to the shocking conclusion that I cannot mount that partition anymore!
I tried some simple things, like mounting on the commandline with different types and editting the fstab. This all didn't work, so yesterday I first made a dd+gzip backup of the partition to prevent further lose.

Now I need the files on that partition, so I'll have to mount it. First I just tried mounting it:
```
root@ubuntu:/home/rikva# mount /dev/hdb2
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
dmesg:

```
[4327521.053000] VFS: Can't find ext3 filesystem on dev hdb2.
```
Some more trying:
```
root@ubuntu:/home/rikva# mount -t ext3 /dev/hdb2 /media/hdb2/
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:/home/rikva# mount -t ext2 /dev/hdb2 /media/hdb2/
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

So I googled on bad superblocks, and I tried to e2fsck: (Sorry it's Dutch)
```
root@ubuntu:/home/rikva# e2fsck -n /dev/hdb2
e2fsck 1.38 (30-Jun-2005)
Kan het ext2-superblok niet vinden, zoeken naar reservekopieën...
e2fsck: Bad magic number in super-block tijdens openen van /dev/hdb2

```
So I tried some different superblocks using e2fsck -b.
I first tried to find the superblock numer by simulating a mke2fs:
```
root@ubuntu:/home/rikva# mke2fs -nj /dev/hdb2
mke2fs 1.38 (30-Jun-2005)
Bestandssysteemlabel=
Soort besturingssysteem: Linux
Blokgrootte=4096 (log=2)
Fragmentgrootte=4096 (log=2)
7684096 inodes, 15360148 blokken
768007 blokken (5.00%) gereserveerd voor de superuser
Eerste gegevensblok=0
469 blokgroepen
32768 blokken per groep, 32768 fragmenten per groep
16384 inodes per groep
Superblokreservekopieën opgeslagen in blokken:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424
```
I tried some different superblocks like this:
```
root@ubuntu:/home/rikva# mount -t ext3 -o sb=98304 /dev/hdb2 /media/hdb2/
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
But none of them work.

What to do?

---

### Post by Sheco on 2005-11-14
:\ maybe it's not on hdb2?

try fdisk again, just to check the disk layout, maybe even try:
```
dmesg | grep hdb
```

---

### Post by Rikva on 2005-11-14
It is on hdb2. 100% sure.
```
rikva@ubuntu:~$ cat /var/log/dmesg | grep hdb;dmesg | grep hdb
[4294670.329000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294670.848000] hdb: WDC WD800JB-00JJA0, ATA DISK drive
[4294674.421000] hdb: max request size: 128KiB
[4294674.425000] hdb: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[4294674.426000] hdb: cache flushes supported
[4294690.081000] VFS: Can't find ext3 filesystem on dev hdb2.
[4328288.900000] VFS: Can't find ext3 filesystem on dev hdb2.
[4328375.720000] VFS: Can't find ext3 filesystem on dev hdb2.
[4328379.066000] VFS: Can't find ext3 filesystem on dev hdb2.
[4328381.839000] VFS: Can't find ext3 filesystem on dev hdb2.
```

Partition layout in fdisk:
```
Schijf /dev/hdb: 80.0 GB, 80026361856 bytes
255 koppen, 63 sectoren/spoor, 9729 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdb1   *           1        2080    16707568+   7  HPFS/NTFS
/dev/hdb2            2081        9729    61440592+  83  Linux
```

---

### Post by Sheco on 2005-11-14
try mounting it as ext2 instead of ext3, just to test.

---

### Post by slux on 2005-11-14
I had a bit similar problem some time ago. Not sure of the cause but it might have something to do with how Linux sees the disk geometry but I only have a hunch and not much more knowledge of the subject.

Anyway, my partition table had ended up a bit broken whatever the cause as well and forensics tools come handy here.

[TestDisk](http://www.cgsecurity.org/index.html?testdisk.html) is a tool you can use to manually search for the actual filesystems inside the disk, it can identify most filesystems just by looking at the raw data and help you reconstruct the partition table. In my case I was able to recover all the data but for some reason couldn't get all the partitions to recover at the same time. Was very glad to get all my data safe anyway.

---

### Post by Rikva on 2005-11-15
[QUOTE=slux]I had a bit similar problem some time ago. Not sure of the cause but it might have something to do with how Linux sees the disk geometry but I only have a hunch and not much more knowledge of the subject.

Anyway, my partition table had ended up a bit broken whatever the cause as well and forensics tools come handy here.

[TestDisk](http://www.cgsecurity.org/index.html?testdisk.html) is a tool you can use to manually search for the actual filesystems inside the disk, it can identify most filesystems just by looking at the raw data and help you reconstruct the partition table. In my case I was able to recover all the data but for some reason couldn't get all the partitions to recover at the same time. Was very glad to get all my data safe anyway.[/QUOTE]
I immediately installed this application. It can see my files and directories on the damaged ext3 partition.
But I'm not sure what to do next. Did you analyze and send the logfiles to the developers, or did you manage to fix it by yourself? If so, could you tell me how?

Edit: The author of this wonderful program has already helped me over mail, and I'm copying my files as I type this reply. Thanks for the support :)

Tip: Don't ever use Partition Magic to edit your data-disk with EXT2 partitions.

---


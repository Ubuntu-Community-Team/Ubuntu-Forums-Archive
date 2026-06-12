---
title: "Device Mapper and nVidia Soft RAID0 (dmraid?)"
date: 2008-09-10
forum: Hardware
---

### Post by icezebra on 2008-09-10
(Bear with me, new to Linux but trying my best!)

Until recently I had two hdrives operating as one under a motherboard (nVidia driver) RAID0 arrangement through dmraid. A few days ago, an automated boot-time disk check ran and on x startup, the raided drive was no longer available. Erk!

 Another potential cause is the installation of truecrypt (since removed), which I understand can also interfere with block devices. There should be one 460GBish NTFS partition.

I don't think this is a problem with dmraid as it still maps the two drives under /dev/mapper/ however /dev/dm-1 no longer exists... I'm really not sure of where to go now. Has anyone experienced this?

Here's some (hopefully helpful) outputs...

icezebra@iz-LPC:~$ uname -a
Linux iz-LPC 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

icezebra@iz-LPC:/$ sudo dmraid -ay -vvv -d
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sde
NOTICE: skipping removable device /dev/sdf
NOTICE: skipping removable device /dev/sdg
NOTICE: skipping removable device /dev/sdh
NOTICE: /dev/sdi: asr discovering
NOTICE: /dev/sdi: ddf1 discovering
NOTICE: /dev/sdi: hpt37x discovering
NOTICE: /dev/sdi: hpt45x discovering
NOTICE: /dev/sdi: isw discovering
NOTICE: /dev/sdi: jmicron discovering
NOTICE: /dev/sdi: lsi discovering
NOTICE: /dev/sdi: nvidia discovering
NOTICE: /dev/sdi: pdc discovering
NOTICE: /dev/sdi: sil discovering
NOTICE: /dev/sdi: via discovering
NOTICE: /dev/sdd: asr discovering
NOTICE: /dev/sdd: ddf1 discovering
NOTICE: /dev/sdd: hpt37x discovering
NOTICE: /dev/sdd: hpt45x discovering
NOTICE: /dev/sdd: isw discovering
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi discovering
NOTICE: /dev/sdd: nvidia discovering
NOTICE: /dev/sdd: pdc discovering
NOTICE: /dev/sdd: sil discovering
NOTICE: /dev/sdd: via discovering
NOTICE: /dev/sdc: asr discovering
NOTICE: /dev/sdc: ddf1 discovering
NOTICE: /dev/sdc: hpt37x discovering
NOTICE: /dev/sdc: hpt45x discovering
NOTICE: /dev/sdc: isw discovering
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi discovering
NOTICE: /dev/sdc: nvidia discovering
NOTICE: /dev/sdc: nvidia metadata discovered
NOTICE: /dev/sdc: pdc discovering
NOTICE: /dev/sdc: sil discovering
NOTICE: /dev/sdc: via discovering
NOTICE: /dev/sdb: asr discovering
NOTICE: /dev/sdb: ddf1 discovering
NOTICE: /dev/sdb: hpt37x discovering
NOTICE: /dev/sdb: hpt45x discovering
NOTICE: /dev/sdb: isw discovering
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi discovering
NOTICE: /dev/sdb: nvidia discovering
NOTICE: /dev/sdb: nvidia metadata discovered
NOTICE: /dev/sdb: pdc discovering
NOTICE: /dev/sdb: sil discoveringicezebra@iz-LPC:~$ ls /dev/mapper
control nvidia_cdjgceeb nvidia_cdjgceeb1

NOTICE: /dev/sdb: via discovering
NOTICE: /dev/sda: asr discovering
NOTICE: /dev/sda: ddf1 discovering
NOTICE: /dev/sda: hpt37x discovering
NOTICE: /dev/sda: hpt45x discovering
NOTICE: /dev/sda: isw discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi discovering
NOTICE: /dev/sda: nvidia discovering
NOTICE: /dev/sda: pdc discovering
NOTICE: /dev/sda: sil discovering
NOTICE: /dev/sda: via discovering
DEBUG: _find_set: searching nvidia_cdjgceeb
DEBUG: _find_set: not found nvidia_cdjgceeb
DEBUG: _find_set: searching nvidia_cdjgceeb
DEBUG: _find_set: not found nvidia_cdjgceeb
NOTICE: added /dev/sdc to RAID set "nvidia_cdjgceeb"
DEBUG: _find_set: searching nvidia_cdjgceeb
DEBUG: _find_set: found nvidia_cdjgceeb
DEBUG: _find_set: searching nvidia_cdjgceeb
DEBUG: _find_set: found nvidia_cdjgceeb
NOTICE: added /dev/sdb to RAID set "nvidia_cdjgceeb"
DEBUG: checking nvidia device "/dev/sdc"
DEBUG: checking nvidia device "/dev/sdb"
DEBUG: set status of set "nvidia_cdjgceeb" to 16
RAID set "nvidia_cdjgceeb" already active
INFO: Activating stripe RAID set "nvidia_cdjgceeb"
NOTICE: discovering partitions on "nvidia_cdjgceeb"
NOTICE: /dev/mapper/nvidia_cdjgceeb: dos discovering
NOTICE: /dev/mapper/nvidia_cdjgceeb: dos metadata discovered
DEBUG: _find_set: searching nvidia_cdjgceeb1
DEBUG: _find_set: not found nvidia_cdjgceeb1
NOTICE: created partitioned RAID set(s) for /dev/mapper/nvidia_cdjgceeb
RAID set "nvidia_cdjgceeb1" already active
INFO: Activating partition RAID set "nvidia_cdjgceeb1"
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "nvidia_cdjgceeb"
DEBUG: freeing device "nvidia_cdjgceeb", path "/dev/sdc"
DEBUG: freeing device "nvidia_cdjgceeb", path "/dev/sdb"
DEBUG: freeing devices of RAID set "nvidia_cdjgceeb1"
DEBUG: freeing device "nvidia_cdjgceeb1", path "/dev/mapper/nvidia_cdjgceeb"

icezebra@iz-LPC:/$ sudo dmraid -ay
RAID set "nvidia_cdjgceeb" already active
RAID set "nvidia_cdjgceeb1" already active

icezebra@iz-LPC:/$ sudo dmraid -b
/dev/sdi: 625142448 total, "VFK201R81XSE0X"
/dev/sdd: 488397168 total, "
/dev/sdc: 488397168 total, "WD-WCANKF417805"
/dev/sdb: 488397168 total, "WD-WCANKF418998"
/dev/sda: 488397168 total, "GEK230T2A86L6B"

icezebra@iz-LPC:/$ sudo dmraid -n
/dev/sdc (nvidia):
0x000 NVIDIA
0x008 size: 30
0x00c chksum: 1259668064
0x010 version: 100
0x012 unitNumber: 0
0x013 reserved: 0
0x014 capacity: 976794112
0x018 sectorSize: 512
0x01c productID: STRIPE 465.77G
0x02c productRevision: 100
0x030 unitFlags: 0
0x034 array->version: 6553668
0x038 array->signature[0]: 452637383
0x03c array->signature[1]: 1089418407
0x040 array->signature[2]: 409592127
0x044 array->signature[3]: 1329789854
0x048 array->raidJobCode: 0
0x049 array->stripeWidth: 2
0x04a array->totalVolumes: 2
0x04b array->originalWidth: 2
0x04c array->raidLevel: 128
0x050 array->stripeBlockSize: 128
0x054 array->stripeBlockByteSize: 65536
0x058 array->stripeBlockPower: 7
0x05c array->stripeMask: 127
0x060 array->stripeSize: 256
0x064 array->stripeByteSize: 131072
0x068 array->raidJobMark 0
0x06c array->originalLevel 128
0x070 array->originalCapacity 976794112
0x074 array->flags 0x1

/dev/sdb (nvidia):
0x000 NVIDIA
0x008 size: 30
0x00c chksum: 1259602528
0x010 version: 100
0x012 unitNumber: 1
0x013 reserved: 0
0x014 capacity: 976794112
0x018 sectorSize: 512
0x01c productID: STRIPE 465.77G
0x02c productRevision: 100
0x030 unitFlags: 0
0x034 array->version: 6553668
0x038 array->signature[0]: 452637383
0x03c array->signature[1]: 1089418407
0x040 array->signature[2]: 409592127
0x044 array->signature[3]: 1329789854
0x048 array->raidJobCode: 0
0x049 array->stripeWidth: 2
0x04a array->totalVolumes: 2
0x04b array->originalWidth: 2
0x04c array->raidLevel: 128
0x050 array->stripeBlockSize: 128
0x054 array->stripeBlockByteSize: 65536
0x058 array->stripeBlockPower: 7
0x05c array->stripeMask: 127
0x060 array->stripeSize: 256
0x064 array->stripeByteSize: 131072
0x068 array->raidJobMark 0
0x06c array->originalLevel 128
0x070 array->originalCapacity 976794112
0x074 array->flags 0x1

icezebra@iz-LPC:~$ ls /dev/mapper
control nvidia_cdjgceeb nvidia_cdjgceeb1

icezebra@iz-LPC:/$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x137852a7

   Device Boot Start End Blocks Id System
/dev/sda1 * 1 30402 244196352 7 HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot Start End Blocks Id System

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8ddf0a0

   Device Boot Start End Blocks Id System
/dev/sdc1 * 1 60803 488394752 7 HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot Start End Blocks Id System
/dev/sdd1 1 30401 244196001 c W95 FAT32 (LBA)

Disk /dev/sdi: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4d89347

   Device Boot Start End Blocks Id System
/dev/sdi1 * 1 37433 300680541 83 Linux
/dev/sdi2 37434 38913 11888100 5 Extended
/dev/sdi5 37434 38913 11888068+ 82 Linux swap / Solaris

icezebra@iz-LPC:/$ dmsetup info -c
/dev/mapper/control: open failed: Permission denied
Failure to communicate with kernel device-mapper driver.
/dev/mapper/control: open failed: Permission denied
Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver
Command failed

icezebra@iz-LPC:~$ dmsetup targets
/dev/mapper/control: open failed: Permission denied
Failure to communicate with kernel device-mapper driver.
/dev/mapper/control: open failed: Permission denied
Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver
Command failed



icezebra@iz-LPC:~$ sudo dmsetup targets
crypt v1.5.0
mirror v1.0.3
striped v1.0.2
linear v1.0.2
error v1.0.1

icezebra@iz-LPC:~$ sudo dmsetup info -c
Name Maj Min Stat Open Targ Event UUID
nvidia_cdjgceeb1 254 1 L--w 0 1 0
nvidia_cdjgceeb 254 0 L--w 1 1 0

If I run:
icezebra@iz-LPC:~$ sudo dmsetup create dm-1 /dev/mapper/nvidia_cdjgceeb --notable

No error comes up and dm-1 is still not in the /dev directory. However, running the next command:

icezebra@iz-LPC:~$ sudo dmsetup info dm-1
Name: dm-1
State: ACTIVE
Tables present: None
Open count: 0
Event number: 0
Major, minor: 254, 2
Number of targets: 0

I'm not sure quite what this all means.... ArrrrrgG

---


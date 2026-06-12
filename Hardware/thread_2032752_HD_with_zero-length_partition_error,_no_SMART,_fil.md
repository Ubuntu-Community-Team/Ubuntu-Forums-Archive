---
title: "HD with zero-length partition error, no SMART, files can be listed"
date: 2012-07-24
forum: Hardware
---

### Post by webkage on 2012-07-24
Hi there.

I have a problem with one of the hard drives.

It is format in ext4 with no encryption.

When mounted, you can see the list the files and folders of the root folder. You can see the size of the files, and data of creation and so on. The folders are shown as empty and the root folder as well says that it has 0 elements despise that you can see it doesn't. When open the directories shows nothing inside, and you can't read the files in the root directory either. I checked cables and put in a different slot. I also tried to mount it in a different OS with the same result.

I tried the following:

_WITH FDISK_

```
sudo fdisk /dev/sdc
sudo fdisk /dev/sdc1
```Said sdc it can't be read.


_With FSCK_

```
fsck.ext4 /dev/sdc , and  
fsck.ext4 -y /dev/sdc
```I got this error:

```
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc
Could this be a zero-length partition?
```_With SMART:_

```
sudo smartctl -i /dev/sdc
``````
Device does not support SMART
``````
sudo smartctl -s on /dev/sdc
``````
unable to fetch IEC (SMART) mode page [unsupported field in scsi command]
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```And that is everything. Any other stuff I found around in this forum either doesn't apply or didn't work.

So my question is if any of you have any suggestion on how to proceed next.

Thanks for your help!

---

### Post by efflandt on 2012-07-24
See what **dmesg | less** or **/var/log/syslog** says about the drive and any read errors or anything.

You might try reconnecting the drive cables or make sure the plugs are seated.

---

### Post by webkage on 2012-07-28
dmesg gives me this:

```
[92788.042532] usb 1-2: new high speed USB device using ehci_hcd and address 7
[92788.203558] usb 1-2: configuration #1 chosen from 1 choice
[92788.204085] scsi6 : SCSI emulation for USB Mass Storage devices
[92788.204229] usb-storage: device found at 7
[92788.204233] usb-storage: waiting for device to settle before scanning
[92793.200143] usb-storage: device scan complete
[92793.242607] scsi 6:0:0:0: Direct-Access     ST350032 0AS                   PQ: 0 ANSI: 2 CCS
[92793.243256] sd 6:0:0:0: Attached scsi generic sg2 type 0
[92793.244829] sd 6:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[92793.245871] sd 6:0:0:0: [sdc] Write Protect is off
[92793.245875] sd 6:0:0:0: [sdc] Mode Sense: 28 00 00 00
[92793.245879] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[92793.247829] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[92793.247835]  sdc: sdc1
[92793.278711] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[92793.278717] sd 6:0:0:0: [sdc] Attached SCSI disk
[92794.812051] EXT4-fs (sdc1): warning: mounting fs with errors, running e2fsck is recommended
[92794.813768] EXT4-fs (sdc1): recovery complete
[92794.813774] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[92812.573349] sd 6:0:0:0: [sdc] Unhandled sense code
[92812.573354] sd 6:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[92812.573359] sd 6:0:0:0: [sdc] Sense Key : Medium Error [current] 
[92812.573365] sd 6:0:0:0: [sdc] Add. Sense: Unrecovered read error
[92812.573370] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 2c 80 01 3f 00 00 10 00
[92812.573382] end_request: I/O error, dev sdc, sector 746586431
[92812.573395] EXT4-fs error (device sdc1): __ext4_get_inode_loc: unable to read inode block - inode=23330817, block=93323296
[92814.099709] sd 6:0:0:0: [sdc] Unhandled sense code
[92814.099714] sd 6:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[92814.099719] sd 6:0:0:0: [sdc] Sense Key : Medium Error [current] 
[92814.099725] sd 6:0:0:0: [sdc] Add. Sense: Peripheral device write fault
[92814.099730] sd 6:0:0:0: [sdc] CDB: Write(10): 2a 00 1d 04 00 3f 00 00 08 00
[92814.099742] end_request: I/O error, dev sdc, sector 486801471
[92814.099747] __ratelimit: 18 callbacks suppressed

```Messages goes repeating for long; pretty much complaining about superblock errors, inodes that can't be read and so on.

I tried in several plugs with different connections; no luck.

---

### Post by webkage on 2012-07-30
I tried to restore a backup superblock but it didn't seem to work at all.

When I do **sudo mke2fs -n /dev/sdc1** I get the list with the alternatives superblocks (sorry for the spanish)

```

mke2fs 1.41.11 (14-Mar-2010)
Etiqueta del sistema de ficheros=
Tipo de SO: Linux
Tamaño del bloque=4096 (bitácora=2)
Tamaño del fragmento=4096 (bitácora=2)
Stride=0 blocks, Stripe width=0 blocks
30531584 nodos-i, 122096000 bloques
6104800 bloques (5.00%) reservados para el superusuario
Primer bloque de datos=0
Número máximo de bloques del sistema de ficheros=4294967296
3727 bloque de grupos
32768 bloques por grupo, 32768 fragmentos por grupo
8192 nodos-i por grupo
Respaldo del superbloque guardado en los bloques: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000

```Anyway, I tried to restore the superblock or to mount the HD using one of the backups and I get the same error. With

[B]sudo e2fsck -f -b 294312 /dev/sdc1

[/B]or[B]

sudo mount -t ext4 -o sb=163840 /dev/sdc1 /mnt[/B]


```
e2fsck: Attempt to read block from filesystem resulted in short read
```And here the dmesg | tail for one of the attempts. 

```

[70957.568359] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 0c 35 00 3f 00 00 02 00
[70957.568371] end_request: I/O error, dev sdc, sector 204800063
[70957.568381] EXT4-fs (sdc1): unable to read superblock
[70983.313609] sd 6:0:0:0: [sdc] Unhandled sense code
[70983.313614] sd 6:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[70983.313619] sd 6:0:0:0: [sdc] Sense Key : Medium Error [current] 
[70983.313625] sd 6:0:0:0: [sdc] Add. Sense: Unrecovered read error
[70983.313630] sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 01 57 00 3f 00 00 02 00
[70983.313642] end_request: I/O error, dev sdc, sector 22478911
[70983.313654] EXT4-fs (sdc1): unable to read superblock

```And again, I can see all the files and metadata. Any hint would be appreciated.

---


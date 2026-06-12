---
title: "Unable to mount Seagate Expansion Drive 1tb i was wondering if anyone knows how to"
date: 2017-01-13
forum: Hardware
---

### Post by g-rover on 2017-01-13
i was wondering if anyone knows how to resolve this problem I am having with my 1 terabyte external seagate hard drive. I believe it has to do with ntfs being placed onto the device by accident. Thank you in advance.

---

### Post by efflandt on 2017-01-13
Ubuntu should not have any problem mounting or accessing ntfs partitions as long as Windows is NOT using "fast boot". However, I don't know if Linux can access it if partition(s) were created as Windows "volumes" instead of partitions.

What does the end of **dmesg** in terminal window (Ctrl+Alt+T) say about the drive when you connect it? Also when it is connected what do you get for: **sudo parted -l** (small L as in list)?

---

### Post by g-rover on 2017-01-13
the end of **dmesg**

[ 8215.402139] sd 8:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 8215.435519]  sdg: sdg1
[ 8215.488204] sd 8:0:0:0: [sdg] Attached SCSI disk
[ 8236.554989] raid6: sse2x1   gen()  1550 MB/s
[ 8236.622940] raid6: sse2x1   xor()  1351 MB/s
[ 8236.690892] raid6: sse2x2   gen()  2476 MB/s
[ 8236.758814] raid6: sse2x2   xor()  2353 MB/s
[ 8236.826773] raid6: sse2x4   gen()  2950 MB/s
[ 8236.894715] raid6: sse2x4   xor()  1526 MB/s
[ 8236.894718] raid6: using algorithm sse2x4 gen() 2950 MB/s
[ 8236.894721] raid6: .... xor() 1526 MB/s, rmw enabled
[ 8236.894725] raid6: using intx1 recovery algorithm
[ 8236.898280] xor: measuring software checksum speed
[ 8236.934668]    prefetch64-sse:  4219.000 MB/sec
[ 8236.974632]    generic_sse:  3964.000 MB/sec
[ 8236.974637] xor: using function: prefetch64-sse (4219.000 MB/sec)
[ 8237.011041] Btrfs loaded
[ 8237.047362] JFS: nTxBlock = 8192, nTxLock = 65536
[ 8237.112021] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[ 9325.358155] perf interrupt took too long (2507 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

---

### Post by g-rover on 2017-01-13
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD6400AAKS-6 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  628GB  628GB   primary  ntfs
 3      628GB   640GB  12.0GB  primary  ntfs         boot


Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 30.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  30.8GB  30.8GB  primary  fat32        boot, lba


Warning: /dev/sdg contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?

---

### Post by ajgreeny on 2017-01-13
No 1TB drive is shown in your output, but I wonder if /dev/sdg is the drive which seems to have a problem with a GPT partition table.
How and why do you thing an ntfs filesystem has been put on it accidentally?

Does your computer boot using BIOS or UEFI?

---

### Post by g-rover on 2017-01-13
bios not uefi it's a damn phoenix award bios[the worst imho] and i'm running ubuntu live off of a usb for my own reasons of security...

---


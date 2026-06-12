---
title: "input/output error read on /dev/sdb"
date: 2009-09-07
forum: Hardware
---

### Post by TpyKv on 2009-09-07
Hi There!

I have replaced the 160GB HDD in my Acer aspire one, with a 400GB Samsung one :)

I have now put the AA1 drive in a 2.5" SATA enclosure, and it is not recognised...

I have installed NTFS-config, and a few other apps, and still, it is not showing up.... tried rebooting with it connected, and still nothing.

Is there anthing you can think of, to get this to work?

gparted gives the error message -  input/output error read on /dev/sdb

Thank you

---

### Post by TpyKv on 2009-09-07
More error messages....

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002bc2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         249     2000061   82  Linux swap / Solaris
/dev/sda2             250       48641   388708740    5  Extended
/dev/sda5             250       48641   388708708+  83  Linux

kevin@acer-aspire-one:~$ dmesg | tail
[ 1172.294688] Buffer I/O error on device sdb, logical block 0
[ 1172.492618] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1172.492639] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1172.492656] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1172.492673] end_request: I/O error, dev sdb, sector 0
[ 1383.728145] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1383.728166] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1383.728183] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1383.728200] end_request: I/O error, dev sdb, sector 2
[ 1383.728268] EXT3-fs: unable to read superblock

kevin@acer-aspire-one:~$ lsusb
Bus 001 Device 004: ID 04fc:0c25 Sunplus Technology Co., Ltd 
Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Anything else I can try?

Thanks in advance!

---

### Post by TpyKv on 2009-09-08
Bump!

I have tried this on Ubuntu (9.04 standard on laptop and netbook remix), also on Windows Vista, Windows 7 RTM, and Mac OSX. 

Ubuntu does not recognise it, at all. If you boot from CD and go to install, it sees the disk, but will not allow you to install. 

Gparted Live CD does not recognise it.

Mac OSX sees it but will not allow you to change anything in the disk utility

Windows (both versions) install the device, but do not list it - when you go into Disk management, it says it is unreadable, again, cannot do anything...

Anymore ideas?

---

### Post by TpyKv on 2009-09-08
kevin@acer-aspire-one:~$ sudo fdisk /dev/sdb
Unable to read /dev/sdb

kevin@acer-aspire-one:~$ sudo fsck /dev/sdb
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

kevin@acer-aspire-one:~$ sudo fsck.ext3 -f /dev/sdb
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

kevin@acer-aspire-one:~$ sudo e2fsck -f /dev/sdb
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

kevin@acer-aspire-one:~$ sudo e2fsck -f -b 8193 /dev/sdb
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

Cannot seem to find a way around this at all.....

---

### Post by TpyKv on 2009-09-09
BUMP

I have tried using a docking station, to see if it was a hardware problem, still no luck...

Anyone?

---

### Post by TpyKv on 2009-09-17
Disk is going in the bin

---

### Post by mrhhug on 2011-07-14
I am running into a similar problem. This disk is a 540.8 MB old disk. yes with a M. This is a disk pulled from a backup computer at a concrete company. This disk controls an entire concrete mixing operation, the guys enter the mixture to be made and this little old 486 gets the job done. I would love to dd the thing onto a new drive and use it that way but i can't access it, ive tried in windows, no go. I've booted off the thing on a my quad core. but i can't read it in windows, so i took it home thinking that gparted would easily read the thing. I can boot off the disk, but i cant read it in windows or in gparted. what am i missing?

---


---
title: "Can't mount external hard drive (USB), Not listed on fdisk"
date: 2008-09-24
forum: Hardware
---

### Post by ShaiI769 on 2008-09-24
Hi There,
Recently iv'e been trying to access an external HD using an IDE/SATA->USB adapter. However when I connect it, it only shows an icon in the "Computer", named USB Drive. When I double click on it is says; "Unable to mount location, can't mount file".

fdisk -l shows only my internal drive, /dev/sda:
```

shai@Lenovo:~$ **sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb3f2be0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         713     5724160   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         713        3297    20754883    7  HPFS/NTFS
/dev/sda3            3298       19457   129805200    5  Extended
/dev/sda5            3298       18795   124487653+  83  Linux
/dev/sda6           18796       19457     5317483+  82  Linux swap / Solaris

```

however, when I list the drives connected, I see sdb. Meaning that for some reason I can't access the partitions:
```

shai@Lenovo:~$ **ls /dev/sd***
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda5  /dev/sda6  /dev/sdb

```

**lsusb** shows when connected:
```

Bus 003 Device 006: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

```

**tail -f /var/log/messages** shows:
```

Sep 24 16:50:39 Lenovo kernel: [ 6822.848339] usb 7-3: new high speed USB device using ehci_hcd and address 11
Sep 24 16:50:39 Lenovo kernel: [ 6822.987477] usb 7-3: configuration #1 chosen from 1 choice
Sep 24 16:50:39 Lenovo kernel: [ 6823.029797] scsi16 : SCSI emulation for USB Mass Storage devices
Sep 24 16:50:44 Lenovo kernel: [ 6828.062918] scsi 16:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
Sep 24 16:50:44 Lenovo kernel: [ 6828.067519] sd 16:0:0:0: [sdb] Attached SCSI disk
Sep 24 16:50:44 Lenovo kernel: [ 6828.067637] sd 16:0:0:0: Attached scsi generic sg2 type 0

```

**dmesg** shows:
```
[ 6822.848339] usb 7-3: new high speed USB device using ehci_hcd and address 11
[ 6822.987477] usb 7-3: configuration #1 chosen from 1 choice
[ 6823.029797] scsi16 : SCSI emulation for USB Mass Storage devices
[ 6823.040781] usb-storage: device found at 11
[ 6823.040781] usb-storage: waiting for device to settle before scanning
[ 6828.058330] usb-storage: device scan complete
[ 6828.062918] scsi 16:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 6828.067519] sd 16:0:0:0: [sdb] Attached SCSI disk
[ 6828.067637] sd 16:0:0:0: Attached scsi generic sg2 type 0

```

Other than that, I can't mount, access to read the external USB HD.
I'm using ubuntu intrepid 8.10, kernel:
```

shai@Lenovo:~$ uname -a
Linux Lenovo 2.6.27-4-generic #1 SMP Wed Sep 24 01:30:51 UTC 2008 i686 GNU/Linux

```


I'm desperate and would really appreciate your help. 

Thanks in advance,
Shai

---

### Post by PgTips on 2008-09-24
Hi, I had a similar problem with a Samsung GT7000. It would not work unless I removed my external USB mouse due to power loading of the USB - this despite the external drive having its own internal power supply (240V AC).
Might not be your problem but worth checking.

Gd Luck

---

### Post by Gonzalo_VC on 2008-10-05
[COLOR="Navy"]Well, I got a WD MyPassport Essential = 160 GB external USB hard-drive, but can't access it neither in Ubuntu/Poseidon nor in winXP... I should get some drivers for the second one, but what about Linux? Any clues?
Maybe one problem is that my "old" machine (with an Atlhon-XP CPU) as only slow USB connections...[/COLOR]

---

### Post by Lobinho on 2009-09-06
Bump.

I have the same problem as ShaiI769.  The hdd in question is a WD500GB caviar blue that was taken from an old desktop whose mainboard died.

Mounting gives the following error:

```
vadmin@vadmin:/dev$ sudo mount sdb /media/recov -v -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Dmesg gives the following:

```
vadmin@vadmin:/dev$ dmesg | tail
[ 4567.389441] usb-storage: device scan complete
[ 4567.395291] scsi 4:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 4567.462854] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 4567.463060] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 4703.427735] EXT4-fs: unable to read superblock
[ 4754.728128] EXT3-fs: unable to read superblock
[ 5381.828178] EXT3-fs: unable to read superblock
[ 5478.596997] EXT2-fs: unable to read superblock
[ 5485.284981] EXT4-fs: unable to read superblock
[ 5498.652190] EXT2-fs: unable to read superblock

```

Bridge details:

```

vadmin@vadmin:/proc$ lsusb
Bus 001 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

vadmin@vadmin:/dev$ cat /proc/scsi/usb-storage/5 
   Host scsi5: usb-storage
       Vendor: JMicron
      Product: USB to ATA/ATAPI Bridge
Serial Number: 152D203380B6
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:

```

Any help is appreciated :)

---

### Post by c9-3Rr0r on 2009-09-06
> **ShaiI769 said:**
> :

```

shai@Lenovo:~$ **ls /dev/sd***
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda5  /dev/sda6  /dev/sdb

```


from that it looks like u don't have any partition on /dev/sdb try
```

sudo fdisk /dev/sdb

```
and then press "p" to print partition table and post output from there

Lobinho did u try
```

sudo fsck /dev/sdb

```
before mounting ?

---

### Post by Lobinho on 2009-09-07
Results of fsck:

```

vadmin@vadmin:~$ sudo fsck /dev/sdb
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Invalid argument while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by VitaLiNux on 2010-01-09
Hello!
I got the same device model as the OP's. Please, should anyone have come up with a solution for a similar problem, please help!

---

### Post by JohnJackson on 2010-01-12
> **PgTips said:**
> Hi, I had a similar problem with a Samsung GT7000. It would not work unless I removed my external USB mouse due to power loading of the USB - this despite the external drive having its own internal power supply (240V AC).
Might not be your problem but worth checking.

Gd Luck

Thanks, just bought one of these from ebuyer and got mine working by removing my mouse. Got to be a bug though?

---

### Post by akamigs on 2010-01-20
did anyone ever solve this problem? im having an identical problem.

---

### Post by Mousie_kebabs on 2010-01-29
Had the same problem with a 60gb Smart Disks.

I tried it plugged into the front usb ports on my tower, I assume these are acting like a hub from one internal port?

Simply plugged into a port on the back of the tower and it worked perfectly.

Checked fdisk -l and it was listed.

Oh, and for an external hard drive without an additional power cable, try a USB cable with a second usb plug on to give extra power from another port, [http://www.amazon.co.uk/Ex-Pro-USB-Cable-Provides-additional/dp/B0019WNMLC]("http://www.amazon.co.uk/Ex-Pro-USB-Cable-Provides-additional/dp/B0019WNMLC")

Mike.

New to the forums :)

---

### Post by fulldecent on 2010-02-15
me too.

also getting:

fdisk: can't read /dev/sdb

that can't be good.

---

### Post by mozart_ar on 2010-07-04
I have same issue.

Deatails:

dmesg:
> Jul  4 13:44:55 ubuntu kernel: [16883.270062] usb 1-2: new high speed USB device using ehci_hcd and address 10
Jul  4 13:44:55 ubuntu kernel: [16883.425667] usb 1-2: configuration #1 chosen from 1 choice
Jul  4 13:44:55 ubuntu kernel: [16883.429449] scsi11 : SCSI emulation for USB Mass Storage devices
Jul  4 13:45:00 ubuntu kernel: [16888.436797] scsi 11:0:0:0: Direct-Access     USB TO I DE/SATA Device   0041 PQ: 0 ANSI: 0
Jul  4 13:45:00 ubuntu kernel: [16888.437364] sd 11:0:0:0: Attached scsi generic sg2 type 0
Jul  4 13:45:00 ubuntu kernel: [16888.441201] sd 11:0:0:0: [sdb] Attached SCSI disk


> sudo fdisk /dev/sdb 

Unable to read /dev/sdb


> lsusb 
Bus 001 Device 010: ID 05e3:0718 Genesys Logic, Inc. 


> uname -a
Linux ubuntu 2.6.32-23-server #37-Ubuntu SMP Fri Jun 11 09:11:11 UTC 2010 x86_64 GNU/Linux


---

### Post by galv on 2010-10-24
> **mozart_ar said:**
> I have same issue.

Deatails:

dmesg:

Same here :( How can I use my external DVD drive (via USB)? Did anyone got it working? I don't have anything else connected by USB.

---

### Post by klaw@mail.com on 2011-03-25
I have the same issue. My external drive is a flash drive, so power cannot be the issue here. The flash drive is new. mkfs.ext4 passed with no error. partprobe is okay too. However, mkfs.ext4 returns error immediately.

How can I format the drive okay, and fsck returns error right after!! 

Am I stuck with FAT32? Please Help!


Karen

root@ubuntu:~# mkfs.ext4  /dev/sdc1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
1966080 inodes, 7864320 blocks
393216 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
240 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 34 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@ubuntu:~# 
root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e0eee9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20922   168054151+   7  HPFS/NTFS
/dev/sda2           20922       28476    60670977    f  W95 Ext'd (LBA)
/dev/sda3           28476       30402    15471800   12  Compaq diagnostics
/dev/sda5           24499       28476    31942656    7  HPFS/NTFS

Disk /dev/sdb: 3963 MB, 3963617280 bytes
128 heads, 63 sectors/track, 960 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2         960     3866624    b  W95 FAT32

Disk /dev/sdc: 34.4 GB, 34359738368 bytes
64 heads, 32 sectors/track, 32768 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000be4a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30721    31457280+  83  Linux
/dev/sdc2           30721       32768     2097135+  82  Linux swap / Solaris
root@ubuntu:~# partprobe
root@ubuntu:~# partprobe -s
/dev/sda: msdos partitions 1 2 <5> 3
/dev/sdb: msdos partitions 1
/dev/sdc: msdos partitions 1 2
root@ubuntu:~# mount /dev/sdc1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# fsck
fsck from util-linux-ng 2.17.2
root@ubuntu:~# fsck -h
fsck from util-linux-ng 2.17.2
root@ubuntu:~# fsck --help
fsck from util-linux-ng 2.17.2
root@ubuntu:~# man fsck
root@ubuntu:~# fsck -t ext4 /dev/sdc1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Superblock has an invalid journal (inode 8).
Clear<y>? no

fsck.ext4: Illegal inode number while checking ext3 journal for /dev/sdc1
root@ubuntu:~# fsck.ext4 /dev/sdc1
e2fsck 1.41.11 (14-Mar-2010)
Superblock has an invalid journal (inode 8).
Clear<y>? no

fsck.ext4: Illegal inode number while checking ext3 journal for /dev/sdc1

---

### Post by OhThatSysOp on 2012-09-10
> **Gonzalo_VC said:**
> [COLOR=Navy]Well, I got a WD MyPassport Essential = 160 GB external USB hard-drive, but can't access it neither in Ubuntu/Poseidon nor in winXP... I should get some drivers for the second one, but what about Linux? Any clues?
Maybe one problem is that my "old" machine (with an Atlhon-XP CPU) as only slow USB connections...[/COLOR]
):P
Your problem isn't the power. if it was a problem, if you put your ear on the hard drive and heard a fading whining sound(PEEEEEEEEEeeeeww) every couple of seconds, that would be the problem. But it IS showing up, isn't it?
[QUOTE=Shail769]
however, when I list the drives connected, I see sdb.
[QUOTE]
So power isn't a problem. Sometimes certain HDD manufacturers don't partition the disk at all, like Seagate and Maxtor, but only if the size is over 10TB.
:popcorn:ANSWER FOR SHAIL::popcorn: Re-format the drive. Depending on the seriousness of the problem, you may even have to download 
OPENSUSE or FEDORA and run the Live Image and partition from there.
(I love smileys, don't you? :3)

:lolflag:ANSWER FOR LOBINHO::lolflag:
if fsck ended like this,
```

vadmin@vadmin:~$ sudo fsck /dev/sdb fsck 1.41.4 (27-Jan-2009) e2fsck 1.41.4 (27-Jan-2009) fsck.ext2: Invalid argument while trying to open /dev/sdb  The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:     e2fsck -b 8193 <device>
```re-format the drive and change the MBR or GUID.
Simple fix, hard to look at.
If you still have problems, let me know.

-OhThatSysOp):P

---

### Post by OhThatSysOp on 2012-09-10
Can you access the data on the flash drive?
Can you read/write?
If you can, don't worry about it.
If you can't, try using XFS, ext4, or ReiserFS. 
I like reiser better, because it's faster and more efficient than ext2, 3, and 4 combined.

---

### Post by rpiche on 2012-11-18
"re-format the drive and change the MBR or GUID."

That's exactly what I need to do but how can it be done. Fdisk and Gparted don't recognize the hard drive. 

Thank you!

---

### Post by rpiche on 2012-11-18
Sorry, didn't mean to post this twice.

"re-format the drive and change the MBR or GUID."

That's exactly what I need to do but how can it be done. Fdisk and Gparted don't recognize the hard drive. 

Thank you!

---

### Post by wildmanne39 on 2012-11-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


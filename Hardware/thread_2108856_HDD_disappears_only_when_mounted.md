---
title: "HDD disappears only when mounted"
date: 2013-01-25
forum: Hardware
---

### Post by sszen on 2013-01-25
I have a problematic Seagate 3TB HDD ST3000DM001-9YN166 in Zentyal-Snapraid setup.

The drive disappears from the system soon after it is mounted, and when it disappears, even Disk Utility cannot see it. Trying to access it from a terminal (e.g. trying to unmount) returns I/O error.

However, if the drive is not mounted, the drive does not disappear (checked up to 7 days) and Disk Utility has no problem accessing its SMART data. SMART shows airflow-related warning in the past, but I doubt that's the reason for falling off the system (only when mounted.)

The HDD is connected to HP SAS Expander which is connected to IBM M1015 (flashed to IT mode.)  I have tried connecting it to a different port on the SAS Expander where another Seagate of the same model was working fine. Rebooting the machine bring back the HDD, until you mount it.

How should I toubleshoot?

hdparm:
```
user@machine:~$ sudo hdparm -I /dev/sdi

/dev/sdi:

ATA device, with non-removable media
        Model Number:       ST3000DM001-9YN166
        Serial Number:      <removed for privacy>
        Firmware Revision:  CC94
        Transport:          Serial, SATA Rev 3.0
Standards:
        Used: unknown (minor revision code 0x0029)
        Supported: 8 7 6 5
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors: 5860533168
        Logical  Sector size:                   512 bytes
        Physical Sector size:                  4096 bytes
        Logical Sector-0 offset:                  0 bytes
        device size with M = 1024*1024:     2861588 MBytes
        device size with M = 1000*1000:     3000592 MBytes (3000 GB)
        cache/buffer size  = unknown
        Nominal Media Rotation Rate: 7200
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = ?
        Advanced power management level: 254
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
           *    Advanced Power Management feature set
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    WRITE_{DMA|MULTIPLE}_FUA_EXT
           *    64-bit World wide name
                Write-Read-Verify feature set
           *    WRITE_UNCORRECTABLE_EXT command
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Segmented DOWNLOAD_MICROCODE
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Gen3 signaling speed (6.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
           *    unknown 76[15]
           *    DMA Setup Auto-Activate optimization
                Device-initiated interface power management
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
                unknown 206[7]
                unknown 206[12] (vendor specific)
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
                supported: enhanced erase
        332min for SECURITY ERASE UNIT. 332min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000c5003532da9f
        NAA             : 5
        IEEE OUI        : 000c50
        Unique ID       : 03532da9f
Checksum: correct
user@machine:~$ 

```smartctl:
```
user@machine:~$ sudo smartctl -i /dev/sdi
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-36-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST3000DM001-9YN166
Serial Number:    Z1F022KK
LU WWN Device Id: 5 000c50 03532da9f
Firmware Version: CC94
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Jan 25 17:48:57 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

user@machine:~$ 

```

---

### Post by Bashing-om on 2013-01-25
sszen; Hi ! Welcome to the forum.

Look at the obvious things first.
1. What is your mount point for the drive?
2. The file system table: post is the output of terminal command:
```
cat /etc/fstab
```3. Compare the output of:
```
mount
``` with the drive mounted and not mounted;
4. Look through the dmesg log /var/log/dmesg with the drive mounted and not mounted, errors ??

If no fault is found here, then maybe bus contention or irq probs ?
[INDENT]just the way I look at it

[/INDENT]

---

### Post by sszen on 2013-01-26
Thanks for the welcome and responding to my question.

The mount point is /media/cv4, and the fstab is as follows. The drive in question is commented out, because the drive disappears soon after getting mounted.

```
user@machine:~$ cat /etc/fstab
#       /etc/fstab:     static  file    system  information.
#
#       Use     'blkid' to      print   the     universally     unique  identifier      for     a
#       device; this    may     be      used    with    UUID=   as      a      more     robust  way     to      name    devices
#       that    works   even    if      disks   are     added   and     removed.See     fstab(5).
#
#       <file   system> <mount  point>  <type>  <options>       <dump>  <pass>
proc    /proc   proc    nodev,noexec,nosuid     0       0
#       /       was     on      /dev/sda1       during  installation
UUID=6d9ae10a-51e5-48f4-ad84-eb4b3cc3fdeb       /       ext4    errors=remount-ro,usrquota,grpquota,acl,user_xattr      0       1
#       swap    was     on      /dev/sda5       during  installation
UUID=49f61a8d-e073-4670-879d-f2f11598724b       none    swap    sw      0      0
none    /run/lock       tmpfs   rw,noexec,nosuid,nodev,size=52428800    0      0
UUID=3184ca13-558c-4962-9667-0022f917e379       /media/p        ext4    defaults0       2
UUID=6c84e608-ba19-4dd1-ac4e-9c17c9cdb258       /media/q        ext4    defaults0       2
UUID=74c1040e-09ba-4fc9-8183-a32ef4a888df       /media/1        ext4    defaults0       2
UUID=9bebd92e-7fab-454d-b632-b0195d690413       /media/3        ext4    defaults0       2
UUID=2683782c-22c1-4a49-93c5-313748c97412       /media/9        ext4    defaults0       2
UUID=a9f0fe85-2d4d-4f59-9551-f295831c5865       /media/cv7      ext4    defaults0       2
UUID=167e63ab-e368-433a-8bbc-3b84e31ce6f3       /media/cv8      ext4    defaults0       2
UUID=715dd4be-7eea-4d43-9072-a211becefeff       /media/3TB-a    ext4    defaults0       2
UUID=56b7b4bb-0621-4bb4-b1de-9dfade5a8f0d       /media/c3a      ext4    defaults0       2
#       UUID=16E0-1237                                  /media/hita-1   vfat   iocharset=utf8   0       0
UUID=281081021080D868                           /media/hita-b   ntfs-3g defaults0       0
UUID=418fcfbf-bd22-4dfb-99ea-0ffe13549dff       /media/cof      ext4    defaults0       2
#       UUID=975033a1-7346-4896-9bda-24f732594a9c       /media/cv4      ext4   defaults 0       2
UUID=c32fa77e-cb81-465d-8015-456370e8cc0e       /media/cv5      ext4    defaults0       2
UUID=888b513f-f38f-4be3-b066-d0077571f73a       /media/cv6      ext4    defaults0       2


user@machine:~$

```When not mounted:
```
user@machine:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,usrquota,grpquota,acl,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=52428800)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/p type ext4 (rw)
/dev/sdc1 on /media/q type ext4 (rw)
/dev/sdn1 on /media/hita-b type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/3 type ext4 (rw)
/dev/sdi1 on /media/3TB-a type ext4 (rw)
/dev/sdh1 on /media/cv5 type ext4 (rw)
/dev/sdf1 on /media/cv6 type ext4 (rw)
/dev/sdo1 on /media/cv8 type ext4 (rw)
/dev/sdl1 on /media/c3a type ext4 (rw)
/dev/sdm1 on /media/cof type ext4 (rw)
/dev/sdk1 on /media/1 type ext4 (rw)
/dev/sdg1 on /media/9 type ext4 (rw)
/dev/sde1 on /media/cv7 type ext4 (rw)
gvfs-fuse-daemon on /home/sokoban/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sokoban)
user@machine:~$

```When mounted (as you can see, ls results in I/O error):
```
user@machine:~$ sudo mount -U 975033a1-7346-4896-9bda-24f732594a9c       /media/cv4
user@machine:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,usrquota,grpquota,acl,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=52428800)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/p type ext4 (rw)
/dev/sdc1 on /media/q type ext4 (rw)
/dev/sdn1 on /media/hita-b type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/3 type ext4 (rw)
/dev/sdi1 on /media/3TB-a type ext4 (rw)
/dev/sdh1 on /media/cv5 type ext4 (rw)
/dev/sdf1 on /media/cv6 type ext4 (rw)
/dev/sdo1 on /media/cv8 type ext4 (rw)
/dev/sdl1 on /media/c3a type ext4 (rw)
/dev/sdm1 on /media/cof type ext4 (rw)
/dev/sdk1 on /media/1 type ext4 (rw)
/dev/sdg1 on /media/9 type ext4 (rw)
/dev/sde1 on /media/cv7 type ext4 (rw)
gvfs-fuse-daemon on /home/sokoban/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sokoban)
/dev/sdj1 on /media/cv4 type ext4 (rw)
user@machine:~$
user@machine:~$ ls /media/cv4
ls: reading directory /media/cv4: Input/output error
user@machine:~$

```I don't see any noteworthy entry in /var/log/dmesg.

I have recreated partition table (GPT) and deleted/recreated partition, but no improvement.

What's the difference between a mounted partition and an umounted drive?  Although SMART seems ok, the HDD (not just the mount point) drops off the system once mounted - might be some bizarre HDD FW bug/HW failure that "raise shield (or perhaps goes in to sleep mode?)" at the first sign of rw access? I mean, even if there were bad sectors and things and ls gets I/O error, shouldn't palimpsest continue to be able to access the HDD's SMART?

---

### Post by Bashing-om on 2013-01-26
sszen;
I also do not see anything obvious; but there should be a space between defaults and 0 in most of your lines -> can not see that as relating to the problem at hand. But maybe that causes them not to be mounted correctly.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) 

Is the UUID correct ?
```
sudo blkid
```In respect to the whole drive dropping out of sight, has the drive ever been in a raid array? Or had a type of "Intel Smart Response Technology" ? Such that metadata  may still be embedded on the disk ?

I would think palimpsest to be able to detect the disk under "most" any circumstance.[INDENT][INDENT]just a thought

[/INDENT][/INDENT]

---

### Post by sszen on 2013-01-27
Regarding fstab, columns are separated by tabs. Using cat command in PuTTY and pasting onto this forum somehow eliminated the ones between default and 0.

The HDD disappeared after mounting for the previous post, so I had to wait until I can reboot the machine. Here is the result, and the UUID seems to match:
```
user@machine:~$ sudo blkid
/dev/sda1: UUID="6d9ae10a-51e5-48f4-ad84-eb4b3cc3fdeb" TYPE="ext4"
/dev/sda5: UUID="49f61a8d-e073-4670-879d-f2f11598724b" TYPE="swap"
/dev/sdb1: UUID="3184ca13-558c-4962-9667-0022f917e379" TYPE="ext4"
/dev/sdc1: UUID="6c84e608-ba19-4dd1-ac4e-9c17c9cdb258" TYPE="ext4"
/dev/sdg1: UUID="2683782c-22c1-4a49-93c5-313748c97412" TYPE="ext4"
/dev/sdk1: LABEL="2of7" UUID="74c1040e-09ba-4fc9-8183-a32ef4a888df" TYPE="ext4"
/dev/sde1: UUID="a9f0fe85-2d4d-4f59-9551-f295831c5865" TYPE="ext4"
/dev/sdd1: LABEL="CopyOf8" UUID="9bebd92e-7fab-454d-b632-b0195d690413" TYPE="ext4"
/dev/sdh1: LABEL="5of9" UUID="c32fa77e-cb81-465d-8015-456370e8cc0e" TYPE="ext4"
/dev/sdo1: UUID="167e63ab-e368-433a-8bbc-3b84e31ce6f3" TYPE="ext4"
/dev/sdf1: LABEL="6of9" UUID="888b513f-f38f-4be3-b066-d0077571f73a" TYPE="ext4"
/dev/sdi1: UUID="715dd4be-7eea-4d43-9072-a211becefeff" TYPE="ext4"
/dev/sdj1: LABEL="4of9" UUID="975033a1-7346-4896-9bda-24f732594a9c" TYPE="ext4"
/dev/sdl1: UUID="56b7b4bb-0621-4bb4-b1de-9dfade5a8f0d" TYPE="ext4"
/dev/sdm1: LABEL="Overflow2TB" UUID="418fcfbf-bd22-4dfb-99ea-0ffe13549dff" TYPE="ext4"
/dev/sdn1: LABEL="EASY DRIVE" UUID="281081021080D868" TYPE="ntfs"
user@machine:~$

```This drive has not been a part of RAID. I came in a Seagate external drive which I used it for several months, and cracked open the shell last month to make it a part of new file server with Snapraid, just like most of the drives that you see in my fstab.

---

### Post by Bashing-om on 2013-01-27
sszen;

Everything seems to match, still don't have a clue what is the cause.
sdj1 = media/cv4 = ***24f732594a9c -> should workie.

Let's see if we can promote some error codes in the dmesg file.
Leave the sdj drive commented out in /etc/fstab and try and mount the drive manually, making up a different mount point to mount the drive to the file system.
```
sudo mkdir /mnt/testing
sudo mount /dev/sdj1 /mnt/testing
```Insure ownership of <some directory> on the mount:
```
sudo chown username:username /mnt/testing/<some directory>
```Once mounted look in the tail of dmesg for system complaints.

There is a cause and ubuntu is great about logging.
[INDENT][INDENT]look'n to see what we can find

[/INDENT][/INDENT]Can you access and manipulate files in the chosen directory ?

---

### Post by sszen on 2013-02-06
There isn't any directory in the drive, so I tried creating one. 
```
user@machine:~$ sudo mkdir /mnt/testing/test 
mkdir: cannot create directory `/mnt/testing/test': Read-only file system 
user@machine:~$    

```And this is the tail of dmesg:
```
[198853.672847] init: ebox.loggerd main process ended, respawning
[276851.599499] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[276851.601317] SGI XFS Quota Management subsystem
[276851.604591] JFS: nTxBlock = 8192, nTxLock = 65536
[276851.613332] NTFS driver 2.1.30 [Flags: R/O MODULE].
[276851.622061] QNX4 filesystem 0.2.3 registered.
[276851.632980] Btrfs loaded
[277075.551673] 8021q: 802.1Q VLAN Support v1.8
[331131.921063] EXT4-fs (sdj1): recovery complete
[331131.921350] EXT4-fs (sdj1): mounted filesystem with ordered data mode. Opts: (null)
[331139.723430] mpt2sas0: log_info(0x31120b10): originator(PL), code(0x12), sub_code(0x0b10)
[331142.716626] mpt2sas0: log_info(0x31120b10): originator(PL), code(0x12), sub_code(0x0b10)
[331145.710647] mpt2sas0: log_info(0x31120b10): originator(PL), code(0x12), sub_code(0x0b10)
[331145.710667] sd 6:0:6:0: [sdj] Unhandled error code
[331145.710670] sd 6:0:6:0: [sdj]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[331145.710674] sd 6:0:6:0: [sdj] CDB: Write(10): 2a 08 ae 84 08 20 00 00 08 00
[331145.710684] end_request: I/O error, dev sdj, sector 2927888416
[331145.710698] end_request: I/O error, dev sdj, sector 2927888416
[331145.710707] sd 6:0:6:0: [sdj] Unhandled error code
[331145.710709] sd 6:0:6:0: [sdj]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[331145.710711] sd 6:0:6:0: [sdj] CDB: Write(10): 2a 00 01 00 09 60 00 00 10 00
[331145.710716] end_request: I/O error, dev sdj, sector 16779616
[331145.710748] Aborting journal on device sdj1-8.
[331145.710785] JBD2: I/O error detected when updating journal superblock for sdj1-8.
[331145.710801] EXT4-fs error (device sdj1) in ext4_init_inode_table:1200: IO failure
[331145.710828] journal commit I/O error
[331145.719412] sd 6:0:6:0: [sdj] Synchronizing SCSI cache
[331145.719438] sd 6:0:6:0: [sdj]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[331145.720498] mpt2sas0: removing handle(0x0010), sas_addr(0x5001438007a0978a)
[331146.259557] mpt2sas0: log_info(0x31110101): originator(PL), code(0x11), sub_code(0x0101)
[331148.963037] mpt2sas0: device is not present handle(0x0010), no sas_device!!!
[331167.633216] EXT4-fs error (device sdj1): ext4_find_entry:935: inode #2: comm chown: reading directory lblock 0
[331190.413506] EXT4-fs error (device sdj1): ext4_journal_start_sb:327: Detected aborted journal
[331190.413511] EXT4-fs (sdj1): Remounting filesystem read-only

```

---


---
title: "Could this be a zero-length partition?"
date: 2013-06-20
forum: Hardware
---

### Post by dileepa1 on 2013-06-20
Hi All,

I have 2x SSD drives and some other drives on an Ubuntu server. This morning the power had gone out at 2 AM and after getting the server up and running, the 2x SSD drives are not mounting. My root, var etc partition are ok (because they are not on the SSD).

I am hoping someone can help me to recover the data from the 1st or 2nd SSD drive. The 1st SSD drive holds a virtual machine and my approach for the backup was to freeze the machine and copy it to the 2nd SDD and then unfreeze the VM. What I didn't do (and should have done) was to copy the VM from the 2nd SSD to an external drive. I have a UPS on the server which didn't shutdown the server gracefully. I thought I would be able to use the 2nd SSD if an error occured on the first but the power outage has taken both SSD's (even though it would be idle at the time). Anyway lessons learnt...

I have gone through the following forum links which mimic the same scenario that I have but I am still at a dead end.

[http://ubuntuforums.org/showthread.php?t=1804435](http://ubuntuforums.org/showthread.php?t=1804435)
[http://askubuntu.com/questions/106054/could-this-be-a-zero-length-error](http://askubuntu.com/questions/106054/could-this-be-a-zero-length-error)
[http://ubuntuforums.org/showthread.php?t=1854308&page=2](http://ubuntuforums.org/showthread.php?t=1854308&page=2)

I believe I am using the ext4 partition with no lvm setup.

The details for my server are as follows:

```

dileepa@server:~$ cat /etc/issue
Ubuntu 10.04.4 LTS \n \l
dileepa@server:~$ uname -a
Linux transcohq 2.6.32-26-generic-pae #48-Ubuntu SMP Wed Nov 24 10:31:20 UTC 2010 i686 GNU/Linux
dileepa@server:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md4 during installation
UUID=73f56bf0-80b7-4dfa-b454-28a194ebc400 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=a8abf5f0-3858-40bd-bec4-5988d5f56e62 /boot           reiserfs notail          0       2
# /tmp was on /dev/md3 during installation
UUID=f4ebe1b2-fb21-4a12-a701-cc07ed627c6b /tmp            reiserfs defaults        0       2
# /var was on /dev/md2 during installation
UUID=b90a41f8-0a59-4421-be3d-b1fdc5db4350 /var            ext3    defaults        0       2
# swap was on /dev/md1 during installation
UUID=84ec317e-2147-4acd-83cb-aa960541c2b4 none            swap    sw              0       0
/dev/sde1    /backup        ext4    defaults        0       2
/dev/sda1    /vm01          ext4    defaults        0       2
/dev/sdb1    /vm02          ext4    defaults        0       2
dileepa@server:~$ ls /dev/sd*
/dev/sda   /dev/sdb   /dev/sdc   /dev/sdc2  /dev/sdc4  /dev/sdc6  /dev/sdd1  /dev/sdd3  /dev/sdd5  /dev/sde
/dev/sda1  /dev/sdb1  /dev/sdc1  /dev/sdc3  /dev/sdc5  /dev/sdd   /dev/sdd2  /dev/sdd4  /dev/sdd6  /dev/sde1

```

So I tried to recover the super block which didnt work:

```

dileepa@server:~$ sudo e2fsck -f /dev/sda1 
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo mke2fs -n /dev/sda1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
7815168 inodes, 31258465 blocks
1562923 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
954 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872

dileepa@server:~$ sudo e2fsck -f -b 32768 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo e2fsck -f -b 32768 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo e2fsck -f -b 98304 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo e2fsck -f -b 163840 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo e2fsck -f -b 229376 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo e2fsck -f -b 294912 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo e2fsck -f -b 819200 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo e2fsck -f -b 884736 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo e2fsck -f -b 1605632 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
dileepa@server:~$ sudo e2fsck -f -b 2654208 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Invalid argument while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

dileepa@server:~$ 

```

I tried testdisk which didnt find any partitions after doing a deep search. I ran the following command but I am not sure where the logs etc are from testdisk to upload it.

```

dileepa@server:~$ sudo testdisk /log /debug /dev/sda
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
TestDisk exited normally.

```

dd is also unable to read the /dev/sda1 partition

```

dileepa@server:~$ sudo dd if=/dev/sda1 of=/dev/null count=8
dd: reading `/dev/sda1': Input/output error
0+0 records in
0+0 records out

```

I tried fixparts and this also was not able to read the MBR

```

dileepa@server:~$ sudo fixparts /dev/sda
FixParts 0.8.4

Loading MBR data from /dev/sda

Unable to read MBR data from '/dev/sda'! Exiting!

```

I also ran the smart tool which is not supported i believe

```

dileepa@server:~$ sudo smartctl -l selftest /dev/sda1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
dileepa@server:~$ sudo smartctl -l selftest /dev/sda1 -T permissive
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Short INQUIRY response, skip product id
Device does not support Self Test logging

```

My 2nd SSD is basically a copy of the 1st SSD with the same partition format of /dev/sdb1 and I have tried the above commands on sdb1 and it also outputs the same results and I am not able to recover the partition information.

Given my scenario, am I able to recover the partition by using any partition recovery program or is there something else I should try?

Thank you in advance.

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by dileepa1 on 2013-06-20
Hi abdullaubuntu,

Thank you for the reply. I tried a reboot of the server and after that I was able to mount the sda1 partition and see the data. However, after about 45 minutes, the errors started to come again and it became the exact same scenario as before. What could this mean? I think I was successful in extracting the VM data files. Is this a hardware issue or do you think i can format the disk and restore that data and see if it is stable?

output from the smartctl command as requested
```
dileepa@server:/backup/192.168.0.201$ sudo smartctl -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)
Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
dileepa@server:/backup/192.168.0.201$ 
dileepa@server:/backup/192.168.0.201$ 
dileepa@server:/backup/192.168.0.201$ 
dileepa@server:/backup/192.168.0.201$ 
dileepa@server:/backup/192.168.0.201$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)
Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
dileepa@server:/backup/192.168.0.201$ 
dileepa@server:/backup/192.168.0.201$ 
dileepa@server:/backup/192.168.0.201$ 
dileepa@server:/backup/192.168.0.201$ sudo smartctl -a /dev/sdb -T  permissive
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)
Short INQUIRY response, skip product id
SMART Health Status: OK
Read defect list: asked for grown list but didn't get it
Error Counter logging not supported
Device does not support Self Test logging
dileepa@server:/backup/192.168.0.201$ sudo smartctl -a /dev/sda -T  permissive
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)
Short INQUIRY response, skip product id
SMART Health Status: OK
Read defect list: asked for grown list but didn't get it
Error Counter logging not supported
Device does not support Self Test logging

```

output of the parted command as requested
```


dileepa@server:/backup/192.168.0.201$ sudo parted -l /dev/sda
[sudo] password for administrator19880912: 
Error: /dev/sda: unrecognised disk label                                  
Error: /dev/sdb: unrecognised disk label                                  
Model: ATA WDC WD2000JS-98M (scsi)
Disk /dev/sdc: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  99.6MB  98.6MB  primary   reiserfs        raid
 2      99.6MB  8099MB  8000MB  primary   linux-swap(v1)  raid
 3      8099MB  128GB   120GB   primary   ext3            raid
 4      128GB   200GB   71.9GB  extended
 5      128GB   138GB   9999MB  logical   reiserfs        raid
 6      138GB   200GB   61.9GB  logical   ext3            raid

Model: ATA WDC WD2000JS-98N (scsi)
Disk /dev/sdd: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  99.6MB  98.6MB  primary   reiserfs        boot, raid
 2      99.6MB  8099MB  8000MB  primary   linux-swap(v1)  raid
 3      8099MB  128GB   120GB   primary   ext3            raid
 4      128GB   200GB   71.9GB  extended
 5      128GB   138GB   9999MB  logical   reiserfs        raid
 6      138GB   200GB   61.9GB  logical   ext3            raid

Model: WD Elements 10A2 (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ext4

Model: Unknown (unknown)
Disk /dev/md2: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End    Size   File system  Flags
 1      0.00B  120GB  120GB  ext3

Model: Unknown (unknown)
Disk /dev/md0: 98.5MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End     Size    File system  Flags
 1      0.00B  98.5MB  98.5MB  reiserfs

Model: Unknown (unknown)
Disk /dev/md3: 9999MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End     Size    File system  Flags
 1      0.00B  9999MB  9999MB  reiserfs

Model: Unknown (unknown)
Disk /dev/md4: 61.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End     Size    File system  Flags
 1      0.00B  61.9GB  61.9GB  ext3

Model: Unknown (unknown)
Disk /dev/md1: 8000MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End     Size    File system     Flags
 1      0.00B  8000MB  8000MB  linux-swap(v1)

```


The errors that appear in the log are:

```

dileepa@server:/backup/192.168.0.201$ tail /var/log/messages
Jun 21 12:41:37 transcohq kernel: [11708.910955] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 bf 00 00 08 00
Jun 21 12:41:37 transcohq kernel: [11708.911387] sd 1:0:0:0: [sda] Unhandled error code
Jun 21 12:41:37 transcohq kernel: [11708.911389] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 21 12:41:37 transcohq kernel: [11708.911392] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
Jun 21 12:41:37 transcohq kernel: [11708.911826] sd 1:0:0:0: [sda] Unhandled error code
Jun 21 12:41:37 transcohq kernel: [11708.911828] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 21 12:41:37 transcohq kernel: [11708.911831] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
Jun 21 12:41:37 transcohq kernel: [11708.912276] sd 1:0:0:0: [sda] Unhandled error code
Jun 21 12:41:37 transcohq kernel: [11708.912278] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 21 12:41:37 transcohq kernel: [11708.912281] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 10 3f 00 00 08 00
dileepa@server:/backup/192.168.0.201$

```


I will reboot the server again and see if I can provide the parted command again.

---

### Post by dileepa1 on 2013-06-20
Hi All,

So after rebooting the server, the mounts become available until i run the e2fsck at which point it reverts back to the partition being at zero length. What should be the approach I should follow?

After the reboot i ran parted and i can see the partition for sda1 and sdb1

```

ileepa@server:~$ sudo parted -l /dev/sda
[sudo] password for administrator19880912: 
Model: ATA OCZ-AGILITY4 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  128GB  128GB  primary  ext4

Model: ATA OCZ-OCTANE S2 (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  128GB  128GB  primary  ext4

Model: ATA WDC WD2000JS-98M (scsi)
Disk /dev/sdc: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  99.6MB  98.6MB  primary   reiserfs        raid
 2      99.6MB  8099MB  8000MB  primary   linux-swap(v1)  raid
 3      8099MB  128GB   120GB   primary   ext3            raid
 4      128GB   200GB   71.9GB  extended
 5      128GB   138GB   9999MB  logical   reiserfs        raid
 6      138GB   200GB   61.9GB  logical   ext3            raid

Model: ATA WDC WD2000JS-98N (scsi)
Disk /dev/sdd: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  99.6MB  98.6MB  primary   reiserfs        boot, raid
 2      99.6MB  8099MB  8000MB  primary   linux-swap(v1)  raid
 3      8099MB  128GB   120GB   primary   ext3            raid
 4      128GB   200GB   71.9GB  extended
 5      128GB   138GB   9999MB  logical   reiserfs        raid
 6      138GB   200GB   61.9GB  logical   ext3            raid

Model: WD Elements 10A2 (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ext4

Model: Unknown (unknown)
Disk /dev/md0: 98.5MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End     Size    File system  Flags
 1      0.00B  98.5MB  98.5MB  reiserfs

Model: Unknown (unknown)
Disk /dev/md3: 9999MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End     Size    File system  Flags
 1      0.00B  9999MB  9999MB  reiserfs

Model: Unknown (unknown)
Disk /dev/md1: 8000MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End     Size    File system     Flags
 1      0.00B  8000MB  8000MB  linux-swap(v1)

Model: Unknown (unknown)
Disk /dev/md2: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End    Size   File system  Flags
 1      0.00B  120GB  120GB  ext3

Model: Unknown (unknown)
Disk /dev/md4: 61.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Number  Start  End     Size    File system  Flags
 1      0.00B  61.9GB  61.9GB  ext3


```

The output form lshw shows that the lastmount was not clean and there are junk characters

```

server
    description: Desktop Computer
    product: MS-7636
    vendor: MSI
    version: 3.0
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-6C626D8811B2
  *-core
       description: Motherboard
       product: H55M-E21(MS-7636)
       vendor: MSI
       physical id: 0
       version: 3.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V17.1 (09/02/2010)
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          slot: CPU 1
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: id=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 4.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 4.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 4.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 4.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 4.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 4.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 4.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 4.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 4.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 4.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 4.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 4.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 4.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 4.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 4.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 4.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 1333 MHz (0.8 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 1333 MHz (0.8 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu:1
          physical id: 1
          bus info: [EMAIL="cpu@1"]cpu@1[/EMAIL]
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: vmx ht cpufreq
          configuration: id=4
        *-logicalcpu:0
             description: Logical CPU
             physical id: 4.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 4.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 4.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 4.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 4.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 4.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 4.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 4.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 4.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 4.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 4.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 4.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 4.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 4.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 4.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 4.10
             capabilities: logical
     *-pci
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 18
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:31 memory:fb800000-fbbfffff memory:d0000000-dfffffff(prefetchable) ioport:dc00(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:fbff6000-fbff600f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:fbff4000-fbff43ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:fbff0000-fbff3fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:e000(size=4096) memory:f0000000-f03fffff ioport:faf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 05
                serial: 6c:62:6d:88:11:b2
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.201 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:30 ioport:e800(size=256) memory:fafff000-faffffff(prefetchable) memory:faff8000-faffbfff(prefetchable)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fbfee000-fbfee3ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:d880(size=8) ioport:d800(size=4) ioport:d480(size=8) ioport:d400(size=4) ioport:d080(size=16) ioport:d000(size=16)
           *-disk:0
                description: ATA Disk
                product: OCZ-AGILITY4
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 1.4.
                serial: OCZ-VYCH8DSO479FR59Y
                size: 119GiB (128GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fa11df32
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: a6c1de5f-b370-4ddb-ba24-f1e86ba26e18
                   size: 119GiB
                   capacity: 119GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-09-29 13:10:39 filesystem=ext4 lastmountpoint=/tmp/vm01ï¿½!ï¿½ï¿½zyï¿½ï¿½ï¿½ï¿½xï¿½ï¿½ï¿½ï¿½ï¿½ï¿½!ï¿½0ï¿½ï¿½ï¿½ï¿½ï¿½~ï¿½!ï¿½ï¿½8ï¿½8ï¿½zyï¿½ï¿½ï¿½ modified=2013-06-21 12:09:40 mounted=2013-06-21 10:34:00 state=clean
           *-disk:1
                description: ATA Disk
                product: OCZ-OCTANE S2
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: 4.14
                serial: OCZ-MKH41M5XH0EOC747
                size: 119GiB (128GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b62b9991
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: 1772cc09-0083-45e6-88ba-39a87657ed5f
                   size: 119GiB
                   capacity: 119GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-09-29 13:11:34 filesystem=ext4 lastmountpoint=/vm02ï¿½G~Tï¿½(ï¿½ï¿½ïï¿½ï¿½+ï¿½@ï¿½ï¿½ï¿½ï¿½Ô&#8230;!ï¿½0ï¿½ï¿½ï¿½ï¿½~ï¿½!ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½(ï¿½ï¿½ïï¿½ï¿½Ô°ï¿½ modified=2013-06-21 01:03:48 mounted=2013-06-21 01:03:48 state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fbfec000-fbfec0ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi2
             logical name: scsi3
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:c880(size=8) ioport:c800(size=4) ioport:c480(size=8) ioport:c400(size=4) ioport:c080(size=16) ioport:c000(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD2000JS-98M
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdc
                version: 02.0
                serial: WD-WCANL1374071
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.6
                   serial: a8abf5f0-3858-40bd-bec4-5988d5f56e62
                   size: 93MiB
                   capacity: 94MiB
                   capabilities: primary multi journaled reiserfs initialized
                   configuration: filesystem=reiserfs hash=r5 state=unclean
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdc2
                   version: 1
                   serial: 84ec317e-2147-4acd-83cb-aa960541c2b4
                   size: 7628MiB
                   capacity: 7629MiB
                   capabilities: primary multi swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sdc3
                   version: 1.0
                   serial: b90a41f8-0a59-4421-be3d-b1fdc5db4350
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary multi journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-12-04 14:17:14 filesystem=ext3 modified=2013-06-21 13:08:23 mounted=2013-06-21 13:08:23 state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sdc4
                   size: 67GiB
                   capacity: 67GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux raid autodetect partition
                      physical id: 5
                      logical name: /dev/sdc5
                      capacity: 9536MiB
                      capabilities: multi
                 *-logicalvolume:1
                      description: Linux raid autodetect partition
                      physical id: 6
                      logical name: /dev/sdc6
                      capacity: 57GiB
                      capabilities: multi
           *-disk:1
                description: ATA Disk
                product: WDC WD2000JS-98N
                vendor: Western Digital
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdd
                version: 10.0
                serial: WD-WCANR1120966
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdd1
                   version: 3.6
                   serial: a8abf5f0-3858-40bd-bec4-5988d5f56e62
                   size: 93MiB
                   capacity: 94MiB
                   capabilities: primary bootable multi journaled reiserfs initialized
                   configuration: filesystem=reiserfs hash=r5 state=unclean
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdd2
                   version: 1
                   serial: 84ec317e-2147-4acd-83cb-aa960541c2b4
                   size: 7628MiB
                   capacity: 7629MiB
                   capabilities: primary multi swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sdd3
                   version: 1.0
                   serial: b90a41f8-0a59-4421-be3d-b1fdc5db4350
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary multi journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-12-04 14:17:14 filesystem=ext3 modified=2013-06-21 13:08:23 mounted=2013-06-21 13:08:23 state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@3:0.0.0,4
                   logical name: /dev/sdd4
                   size: 67GiB
                   capacity: 67GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux raid autodetect partition
                      physical id: 5
                      logical name: /dev/sdd5
                      capacity: 9536MiB
                      capabilities: multi
                 *-logicalvolume:1
                      description: Linux raid autodetect partition
                      physical id: 6
                      logical name: /dev/sdd6
                      capacity: 57GiB
                      capabilities: multi
     *-scsi
          physical id: 2
          bus info: usb@1:1.4
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Elements 10A2
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sde
             version: 1033
             serial: WX11A13D7585
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=6 signature=0004a183
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sde1
                logical name: /backup
                version: 1.0
                serial: 6a0b9c80-a876-4cb7-8629-ffedb9558544
                size: 465GiB
                capacity: 465GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-03-20 21:05:26 filesystem=ext4 lastmountpoint=/backupï&#376;£ï¿½ï¿½,ï¿½ï¿½ï¿½ï¿½>ï¿½ï¿½!ï¿½8ï¿½ï¿½Bï¿½8ï¿½ï¿½ï¿½0ï¿½ï¿½0ï¿½ï¿½ï¿½>ï¿½ modified=2013-06-21 13:08:14 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2013-06-21 13:08:14 state=mounted
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh

```

finally, this is what I observed when i ran the e2fsch after a reboot:

```


dileepa@server:~$ sudo e2fsck -f /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 88/7815168 files (3.4% non-contiguous), 15346193/31258465 blocks
dileepa@server:~$ sudo e2fsck -f /dev/sdb1
e2fsck 1.41.11 (14-Mar-2010)
/dev/sdb1: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Error reading block 1004 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes
Force rewrite<y>? yes
Error reading block 1005 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes
Force rewrite<y>? yes
Error reading block 1006 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes
Force rewrite<y>? yes
Error reading block 1007 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes
Force rewrite<y>? yes
Error reading block 1008 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes
Force rewrite<y>? yes
Error reading block 1009 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes
Force rewrite<y>? 
/dev/sdb1: e2fsck canceled.
dileepa@server:~$ sudo e2fsck -f /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

```

---

### Post by dileepa1 on 2013-06-20
Hi All,

I rebooted the server again and now the 2 mounts are no longer showing up under /dev/sd* and my other drives have taken over the place of /dev/sda1 etc. I think the drives are dead. The servers are in a remote location to me so I am not able to see if they are spinning. 

Is there anything else I should do before giving up on the 2 SSD drives? They are both 128 GB and less than 8 months old.

-Dileepa

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by dileepa1 on 2013-06-21
Hi ahallubuntu,

I agree with your assessment and I too was surprised when both drives stopped working. There was a lot of people waiting on me to get the VM up so I was able to use the backup copy I luckly manages to get this morning.

I am interested to try a reformat of the drives but how can I do this is they no longer appear under /dev?

Once again...before it was:

```

dileepa@server:~$ ls /dev/sd*
/dev/sda   /dev/sdb   /dev/sdc   /dev/sdc2  /dev/sdc4  /dev/sdc6  /dev/sdd1  /dev/sdd3  /dev/sdd5  /dev/sde /dev/sda1  /dev/sdb1  /dev/sdc1  /dev/sdc3  /dev/sdc5  /dev/sdd   /dev/sdd2  /dev/sdd4  /dev/sdd6  /dev/sde1


```

and after restarting the server for the 4th time i am left with:

```

dileepa@server:~$ ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sda4  /dev/sda6  /dev/sdb1  /dev/sdb3  /dev/sdb5  /dev/sdc
/dev/sda1  /dev/sda3  /dev/sda5  /dev/sdb   /dev/sdb2  /dev/sdb4  /dev/sdb6  /dev/sdc1

```

I did an lshw which confirmed that the SSD drives are not detected. If its not recoverable then I will try to get a replacement as your correct in that they are under warranty.

---


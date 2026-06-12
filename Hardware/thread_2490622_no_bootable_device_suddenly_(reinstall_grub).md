---
title: "no bootable device suddenly (reinstall grub?)"
date: 2023-09-09
forum: Hardware
---

### Post by bjlockie on 2023-09-09
My acer aspire a515-55 laptop froze so I powered it off and it won't boot now.
It says there is no bootable device.
I booted lubuntu off USB and ran KDE Partition Manager.
It shows the drive.
Does it look like reinstalling grub will fix it?

[ATTACH=CONFIG]292709[/ATTACH]

---

### Post by tea for one on 2023-09-10
> **bjlockie said:**
> Does it look like reinstalling grub will fix it?
Possibly, difficult to be precise.
Sometimes, after an ungraceful power off, the file systems become damaged.

First, I would boot into a live session and check the file systems.
It might simply be your ESP needs a "dirty bit" cleaned?

Second, you can boot UEFI systems with a little utility stored on a flash drive.
Have a look at rEFInd
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
You can create a portable USB boot device [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

---

### Post by bjlockie on 2023-09-10
> $ sudo fsck /dev/nvme0n1p2
fsck from util-linux 2.38.1
e2fsck 1.47.0 (5-Feb-2023)
lubuntu_nvme: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? yes
fsck.ext4: Input/output error while recovering journal of lubuntu_nvme
fsck.ext4: unable to set superblock flags on lubuntu_nvme


lubuntu_nvme: ********** WARNING: Filesystem still has errors **********


$ sudo smartctl -a /dev/nvme0n1
smartctl 7.3 2022-02-28 r5338 [x86_64-linux-6.2.0-20-generic] (local build)
Copyright (C) 2002-22, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Number:                       KINGSTON RBUSNS8154P3128GJ1
Serial Number:                      50026B7684581795
Firmware Version:                   E8FK12.3
PCI Vendor/Subsystem ID:            0x2646
IEEE OUI Identifier:                0x0026b7
Total NVM Capacity:                 128,035,676,160 [128 GB]
Unallocated NVM Capacity:           0
Controller ID:                      0
NVMe Version:                       1.2
Number of Namespaces:               1
Namespace 1 Size/Capacity:          128,035,676,160 [128 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            0026b7 6845817955
Local Time is:                      Sun Sep 10 19:40:39 2023 UTC
Firmware Updates (0x12):            1 Slot, no Reset required
Optional Admin Commands (0x0007):   Security Format Frmw_DL
Optional NVM Commands (0x001e):     Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat
Log Page Attributes (0x04):         Ext_Get_Lg
Maximum Data Transfer Size:         512 Pages
Warning  Comp. Temp. Threshold:     84 Celsius
Critical Comp. Temp. Threshold:     88 Celsius

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     7.90W  0.0790W       -    0  0  0  0      600     600
 1 +     7.90W  0.0790W       -    0  0  0  0      600     600
 2 +     7.90W  0.0790W       -    0  0  0  0      600     600
 3 -   0.1000W  0.0790W       -    3  3  3  3     1000    1000
 4 -   0.0050W  0.0790W       -    4  4  4  4   400000   90000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         1
 1 -    4096       0         0

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        40 Celsius
Available Spare:                    100%
Available Spare Threshold:          100%
Percentage Used:                    2%
Data Units Read:                    3,357,232 [1.71 TB]
Data Units Written:                 2,723,933 [1.39 TB]
Host Read Commands:                 39,310,664
Host Write Commands:                44,263,688
Controller Busy Time:               71
Power Cycles:                       725
Power On Hours:                     174
Unsafe Shutdowns:                   14
Media and Data Integrity Errors:    0
Error Information Log Entries:      1,013
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 2:               40 Celsius

Error Information (NVMe Log 0x01, 16 of 16 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0       1013     4  0xb081  0x0305      -            0     1     -
  1       1012     4  0xa081  0x0305      -            0     1     -
  2       1011     4  0x9081  0x0305      -            0     1     -
  3       1010     4  0x8081  0x0305      -            0     1     -
  4       1009     4  0x7081  0x0305      -            0     1     -
  5       1008     4  0x6081  0x0305      -            0     1     -
  6       1007     4  0x5080  0x0305      -            0     1     -
  7       1006     4  0x4080  0x0305      -            0     1     -
  8       1005     4  0x3080  0x0305      -            0     1     -
  9       1004     4  0x2080  0x0305      -            0     1     -
 10       1003     4  0x1080  0x0305      -            0     1     -
 11       1002     4  0x0080  0x0305      -            0     1     -
 12       1001     2  0x5340  0x0305      -            0     1     -
 13       1000     2  0x4340  0x0305      -            0     1     -
 14        999     2  0x3340  0x0305      -            0     1     -
 15        998     2  0x2340  0x0305      -            0     1     -


$ sudo fsck -f /dev/nvme0n1p2
fsck from util-linux 2.38.1
e2fsck 1.47.0 (5-Feb-2023)
lubuntu_nvme: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? no
Clear journal<y>? yes
fsck.ext4: Input/output error while recovering journal of lubuntu_nvme
fsck.ext4: unable to set superblock flags on lubuntu_nvme


lubuntu_nvme: ********** WARNING: Filesystem still has errors **********



It seems like drive is dead yet smartctl says it's ok.
Can I fix it without reinstalling?
If I do have to reinstall should I use a different drive?

---

### Post by bjlockie on 2023-09-10
I ended up replacing the drive.

SMART says the drive is fine but I can't write to it:

> $ sudo smartctl -a /dev/nvme0n1
smartctl 7.3 2022-02-28 r5338 [x86_64-linux-6.2.0-20-generic] (local build)
Copyright (C) 2002-22, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Number:                       KINGSTON RBUSNS8154P3128GJ1
Serial Number:                      50026B7684581795
Firmware Version:                   E8FK12.3
PCI Vendor/Subsystem ID:            0x2646
IEEE OUI Identifier:                0x0026b7
Total NVM Capacity:                 128,035,676,160 [128 GB]
Unallocated NVM Capacity:           0
Controller ID:                      0
NVMe Version:                       1.2
Number of Namespaces:               1
Namespace 1 Size/Capacity:          128,035,676,160 [128 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            0026b7 6845817955
Local Time is:                      Sun Sep 10 19:40:39 2023 UTC
Firmware Updates (0x12):            1 Slot, no Reset required
Optional Admin Commands (0x0007):   Security Format Frmw_DL
Optional NVM Commands (0x001e):     Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat
Log Page Attributes (0x04):         Ext_Get_Lg
Maximum Data Transfer Size:         512 Pages
Warning  Comp. Temp. Threshold:     84 Celsius
Critical Comp. Temp. Threshold:     88 Celsius

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     7.90W  0.0790W       -    0  0  0  0      600     600
 1 +     7.90W  0.0790W       -    0  0  0  0      600     600
 2 +     7.90W  0.0790W       -    0  0  0  0      600     600
 3 -   0.1000W  0.0790W       -    3  3  3  3     1000    1000
 4 -   0.0050W  0.0790W       -    4  4  4  4   400000   90000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         1
 1 -    4096       0         0

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        40 Celsius
Available Spare:                    100%
Available Spare Threshold:          100%
Percentage Used:                    2%
Data Units Read:                    3,357,232 [1.71 TB]
Data Units Written:                 2,723,933 [1.39 TB]
Host Read Commands:                 39,310,664
Host Write Commands:                44,263,688
Controller Busy Time:               71
Power Cycles:                       725
Power On Hours:                     174
Unsafe Shutdowns:                   14
Media and Data Integrity Errors:    0
Error Information Log Entries:      1,013
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 2:               40 Celsius

Error Information (NVMe Log 0x01, 16 of 16 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0       1013     4  0xb081  0x0305      -            0     1     -
  1       1012     4  0xa081  0x0305      -            0     1     -
  2       1011     4  0x9081  0x0305      -            0     1     -
  3       1010     4  0x8081  0x0305      -            0     1     -
  4       1009     4  0x7081  0x0305      -            0     1     -
  5       1008     4  0x6081  0x0305      -            0     1     -
  6       1007     4  0x5080  0x0305      -            0     1     -
  7       1006     4  0x4080  0x0305      -            0     1     -
  8       1005     4  0x3080  0x0305      -            0     1     -
  9       1004     4  0x2080  0x0305      -            0     1     -
 10       1003     4  0x1080  0x0305      -            0     1     -
 11       1002     4  0x0080  0x0305      -            0     1     -
 12       1001     2  0x5340  0x0305      -            0     1     -
 13       1000     2  0x4340  0x0305      -            0     1     -
 14        999     2  0x3340  0x0305      -            0     1     -
 15        998     2  0x2340  0x0305      -            0     1     -


$ sudo fsck -f /dev/nvme0n1p2
fsck from util-linux 2.38.1
e2fsck 1.47.0 (5-Feb-2023)
lubuntu_nvme: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? no
Clear journal<y>? yes
fsck.ext4: Input/output error while recovering journal of lubuntu_nvme
fsck.ext4: unable to set superblock flags on lubuntu_nvme


lubuntu_nvme: ********** WARNING: Filesystem still has errors **********


Create a new partition (300.00 MiB, fat32) on &#8216;/dev/nvme0n1&#8217;


Job: Create new partition on device &#8216;/dev/nvme0n1&#8217;


Command: sfdisk --force --append /dev/nvme0n1

Failed to add partition &#8216;New Partition&#8217; to device &#8216;/dev/nvme0n1&#8217;.

Failed to add partition &#8216;New Partition&#8217; to device &#8216;/dev/nvme0n1&#8217;.


KDE Partition Manager (delete partitions):
Delete partition &#8216;/dev/nvme0n1p1&#8217; (300.00 MiB, fat32) 
Job: Delete file system on &#8216;/dev/nvme0n1p1&#8217; 
Command: wipefs --all /dev/nvme0n1p1 
Delete file system on &#8216;/dev/nvme0n1p1&#8217;: Success

Job: Delete the partition &#8216;/dev/nvme0n1p1&#8217; 
Command: sfdisk --force --delete /dev/nvme0n1 1 

Could not delete partition &#8216;/dev/nvme0n1&#8217;. 

Could not delete partition &#8216;/dev/nvme0n1p1&#8217;. 
Delete the partition &#8216;/dev/nvme0n1p1&#8217;: Error
Delete partition &#8216;/dev/nvme0n1p1&#8217; (300.00 MiB, fat32): Error


# delete partition with fdisk
sudo fdisk /dev/nvme0n1

Disk /dev/nvme0n1: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk model: KINGSTON RBUSNS8154P3128GJ1             
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 3C4BDD63-2DE1-A340-9942-242D3717D789

Command (m for help): wq
fdisk: failed to write disklabel: No data available


---

### Post by yancek on 2023-09-11
>  Unsafe Shutdowns:                   14

The above line is from your smartctl output and unsafely shutting down that often can definitely create problems.  If you do that, the partition is not unmounted correctly which creates problems.  See the link below on 'dirty bit' and what it is/does.

[https://askubuntu.com/questions/1202010/fsck-dirty-bit-reported](https://askubuntu.com/questions/1202010/fsck-dirty-bit-reported)

A method used to safely shut down when the computer freezes is to simultaneously hold down the Alt key and the prtsc key, while doing that consecutively type the letters r e i s u b and it should shut down.  You don't need to do this in a terminal or even have one open.  Always works for me.

---

### Post by bjlockie on 2023-09-11
> **yancek said:**
> 
A method used to safely shut down when the computer freezes is to simultaneously hold down the Alt key and the prtsc key, while doing that consecutively type the letters r e i s u b and it should shut down.  You don't need to do this in a terminal or even have one open.  Always works for me.

I didn't know you could do this.
Why don't they just do it on ctrl-alt-del?

---

### Post by yancek on 2023-09-12
Ctrl+Alt+ Del I would expect would be better than shutting down by pressing the power button.  REISUB is a series of commands which are all explained at the Arch Wiki at the link below:

  [https://wiki.archlinux.org/title/keyboard_shortcuts](https://wiki.archlinux.org/title/keyboard_shortcuts)

You can also use the same method with reisuo which will shut down rather than reboot.
If your screen is freezing/locking, you might investigate using the kill command to stop a process.

 [https://www.cyberciti.biz/faq/how-to-check-running-process-in-linux-using-command-line/](https://www.cyberciti.biz/faq/how-to-check-running-process-in-linux-using-command-line/)

Or the link below:

[https://www.maketecheasier.com/restart-frozen-desktop-linux/](https://www.maketecheasier.com/restart-frozen-desktop-linux/)

---


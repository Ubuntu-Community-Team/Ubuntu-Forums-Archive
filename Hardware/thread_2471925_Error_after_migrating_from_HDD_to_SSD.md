---
title: "Error after migrating from HDD to SSD"
date: 2022-02-13
forum: Hardware
---

### Post by manmath on 2022-02-13
My hard drive was very slow (perhaps slowest). So, this morning I cloned that to an SSD and scrapped that HDD.
Now my system boots fine. But I see the following errors. Please suggest if it's serious, and is there any way to fix?
The errors are:

[2.243969] systemd[1]: Journal Audit Socket was skipped because of a failed condition check (ConditionSecurity=audit).
[2.246592] systemd[1]: Kernel Trace File System was skipped because of a failed condition check (ConditionPathExists=/sys/kernel/tracing).
[2.250166] systemd[1]: File System Check on Root Device was skipped because of a failed condition check (ConditionPathExists=!/run/initramfs/fsck-root).
[2.254915] systemd[1]: Repartition Root Disk was skipped because all trigger condition checks failed.
[2.270877] systemd[1]: Platform Persistent Storage Archival was skipped because of a failed condition check (ConditionDirectoryNotEmpty=/sys/fs/pstore).

---

### Post by TheFu on 2022-02-13
Are the sector sizes the same between the SSD and HDD?

Was the SSD "burned in" some before use?  I like to use SSDs for junk data for a few months before trusting them.  I've seen quality model/brand SSDs fail completely after 1 month of use. Replacement under warranty wasn't hard, but it was a hassle. The replacement has been working fine a few years now.

When moving an OS to new storage, I start with a fresh install of the desired OS/release, then restore my normal backups onto it. This avoids all sorts of issues and provides a clean OS to build on.

Also, you should check the SMART data on the disk. See what the drive says about itself.

---

### Post by manmath on 2022-02-13
Hard drive was of 80GB. SSD is brand new, of 240GB.

---

### Post by linux-sysop on 2022-02-13
I use Gparted for large partition migrations.  I copy and paste them and never ran into an issue. How did you clone or ghost your HD to the SSD? 

As TheFu suggested, it could be you got the unlucky lemon, the minority of these SSD ever fail out of the box.  I have 2 SSD in my machine and the original spin drive that came with the machine.  

A friend gave me 2 WD Black 2 TB HDs only 6 months old. He replaced them on his Windows PC with a 10 TB HD.  I use them only for large file migrations as the WD Black is a toaster oven.  These are made for gamers, I would paste a heatsink and a cooling fan on them, if I were to use them as permanent drives. After a 4 hours session of juggling partitions to another drive the WD Black metal was almost hot enough to burn the skin.  It startled me when I touched it, and it wasn't even inside my PC during the process.  I am not a big advocate of the WD Black HD.  Meanwhile my friend says his new WD Black 10 TB drive is functional. 

If you can acquire or borrow another HD, I would off load the files and try again.  Otherwise, back up your important data to DVD, get a RMA (return materials authorization) from the manufacturer of the SSD, and ship it back.  I did this once with a GPU card from MSI and the shipping was paid by them at the UPS store. Had to wait a week for the replacement GPU to arrive.  I even got a memory upgrade from 1 GB to 2 GB at no charge.

--Editing starts here--
Do I need to say, back up your data if possible?

You can do this Live boot from USB thumb drive or CD, try a fsck on the device.  Here is a guide: [https://linuxhandbook.com/fsck-command/](https://linuxhandbook.com/fsck-command/)

This should assist in finding the fault or repairing file errors on the drive.  

Another thing I have done, with Linux OS is paint over the top with the Live boot.  This would be my** last resort **before throwing in the towel.
**ONLY DO THIS IF YOU HAVE EXHAUSTED ALL OTHER AVENUES**

[LIST]
[*]Install from Live boot, choose do something else option, and do not format the drive.
[*]Only show it the / (root mount point) and allow it to reinstall over the top of the current install.
[*]Should this work, you need to upgrade the system once it boots.
[/LIST]

Hopefully someone else has additional and better advice than I can give you at this time.

---

### Post by TheFu on 2022-02-13
> **manmath said:**
> Hard drive was of 80GB. SSD is brand new, of 240GB.

But what are the sector sizes?  It is extremely likely that both are 512b sectors, based strictly on the sizes, but we don't know unless you check.

---

### Post by manmath on 2022-02-13
Thanks @TheFu and @linux-sysop, here's some more info: I used clonezilla to do device-to-device clone. Please suggest me what do those error messages mean and if they are fatal. For now, the system is running fine. Boot times and system responsiveness have increased multifold. I'm just worried about those error messages. You know, just to be safe than sorry in future.

---

### Post by TheFu on 2022-02-13
I don't know. I wouldn't trust the storage until I'd looked up each of those messages and understood what they mean.
I've never used clonezilla. No clue what caveats it has.  Cloning a corrupted disk results in corrupted data/file systems on the target.  Also, the OS installs specific optimizations for different types of storage.  I don't know if that will be enabled if a clone is made or not (switching from spinning rush HDD to SSD).  IDK.

If it were me, I'd do like I said above ....

> When moving an OS to new storage, I start with a **fresh install** of the desired OS/release, then **restore my normal backups** onto it. This avoids all sorts of issues and provides a clean OS to build on.

---

### Post by manmath on 2022-02-15
Backed up data. Did a fresh install. The error messages are still there.

---

### Post by TheFu on 2022-02-15
> **manmath said:**
> Backed up data. Did a fresh install. The error messages are still there.

I'd suspect a hardware issue somewhere. Could be the SSD, controller, cables.  What does the SMART data show?

---

### Post by manmath on 2022-02-15
SMART data shows good:
root@manmath:~# skdump --help
Usage: skdump [PARAMETERS] DEVICE
Reads ATA SMART data from a device and parses it.

        --overall               Show overall status
        --status                Show SMART status
        --can-smart             Show whether SMART is supported
        --power-on              Print power on time in ms
        --power-cycle           Print number of power cycles
        --bad                   Print bad sector count
        --temperature           Print drive temperature in mKelvin
        --save[=FILENAME]       Save raw data to file/STDOUT
        --load[=FILENAME]       Read data from a file/STDIN instead of device
        -h | --help             Show this help
root@manmath:~# skdump --overall /dev/sda
**GOOD**

---

### Post by TheFu on 2022-02-16
That isn't SMART data.  Please use **smartctl** to gather the details after running a short test.  **-t short** is the short test option.

---

### Post by manmath on 2022-02-17
smartctl results:

```
root@manmath:~# smartctl -t short /dev/sda
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.16.9-zen1] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Fri Feb 18 07:55:42 2022 IST
Use smartctl -X to abort test.
```
```
root@manmath:~# smartctl -a /dev/sda
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.16.9-zen1] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Crucial/Micron Client SSDs
Device Model:     CT240BX500SSD1
Serial Number:    2050E4DCA8AD
LU WWN Device Id: 5 00a075 1e4dca8ad
Firmware Version: M6CR041
User Capacity:    240,057,409,536 bytes [240 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
TRIM Command:     Available
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-3 T13/2161-D revision 4
SATA Version is:  SATA 3.3, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Feb 18 07:56:49 2022 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x02) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  120) seconds.
Offline data collection
capabilities:                    (0x11) SMART execute Offline immediate.
                                        No Auto Offline data collection support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0002) Does not save SMART data before
                                        entering power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  10) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   000    Pre-fail  Always       -       0
  5 Reallocate_NAND_Blk_Cnt 0x0032   100   100   010    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       699
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       569
171 Program_Fail_Count      0x0032   100   100   000    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   100   100   000    Old_age   Always       -       0
173 Ave_Block-Erase_Count   0x0032   099   099   000    Old_age   Always       -       11
174 Unexpect_Power_Loss_Ct  0x0032   100   100   000    Old_age   Always       -       40
180 Unused_Reserve_NAND_Blk 0x0033   100   100   000    Pre-fail  Always       -       28
183 SATA_Interfac_Downshift 0x0032   100   100   000    Old_age   Always       -       0
184 Error_Correction_Count  0x0032   100   100   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   066   049   000    Old_age   Always       -       34 (Min/Max 21/51)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_ECC_Cnt 0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       0
202 Percent_Lifetime_Remain 0x0030   099   099   001    Old_age   Offline      -       1
206 Write_Error_Rate        0x000e   100   100   000    Old_age   Always       -       0
210 Success_RAIN_Recov_Cnt  0x0032   100   100   000    Old_age   Always       -       0
246 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       1556679048
247 Host_Program_Page_Count 0x0032   100   100   000    Old_age   Always       -       48646220
248 FTL_Program_Page_Count  0x0032   100   100   000    Old_age   Always       -       44352048
249 Unkn_CrucialMicron_Attr 0x0032   100   100   000    Old_age   Always       -       0
250 Read_Error_Retry_Rate   0x0032   100   100   000    Old_age   Always       -       0
251 Unkn_CrucialMicron_Attr 0x0032   100   100   000    Old_age   Always       -       2029423217
252 Unkn_CrucialMicron_Attr 0x0032   100   100   000    Old_age   Always       -       0
253 Unkn_CrucialMicron_Attr 0x0032   100   100   000    Old_age   Always       -       0
254 Unkn_CrucialMicron_Attr 0x0032   100   100   000    Old_age   Always       -       49
223 Unkn_CrucialMicron_Attr 0x0032   100   100   000    Old_age   Always       -       1

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       699         -

```
```
root@manmath:~# smartctl -l selftest /dev/sda
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.16.9-zen1] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       699         -
```

---

### Post by juxwillx on 2022-02-18
Check whather the SSD is faulty or not and what are the sector sizes btw?

---

### Post by manmath on 2022-02-18
> **juxwillx said:**
> Check whather the SSD is faulty or not and what are the sector sizes btw?
```
root@manmath:~# fdisk -l
Disk /dev/sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk model: CT240BX500SSD1  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7da84acd

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 468860927 468858880 223.6G 83 Linux
```

---

### Post by TheFu on 2022-02-18
So we have confirmation that sectors are 512b, as suspected.  Now we know THAT sector alignment isn't an issue.

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       699
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       569
173 Ave_Block-Erase_Count   0x0032   099   099   000    Old_age   Always       -       11
174 Unexpect_Power_Loss_Ct  0x0032   100   100   000    Old_age   Always       -       40
180 Unused_Reserve_NAND_Blk 0x0033   100   100   000    Pre-fail  Always       -       28
194 Temperature_Celsius     0x0022   066   049   000    Old_age   Always       -       34 (Min/Max 21/51)
202 Percent_Lifetime_Remain 0x0030   099   099   001    Old_age   Offline      -       1
246 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       1556679048
247 Host_Program_Page_Count 0x0032   100   100   000    Old_age   Always       -       48646220
248 FTL_Program_Page_Count  0x0032   100   100   000    Old_age   Always       -       44352048
251 Unkn_CrucialMicron_Attr 0x0032   100   100   000    Old_age   Always       -       2029423217
254 Unkn_CrucialMicron_Attr 0x0032   100   100   000    Old_age   Always       -       49
223 Unkn_CrucialMicron_Attr 0x0032   100   100   000    Old_age   Always       -       1
```
Are the interesting values to be researched.  Nothing jumps out, except all the #174 events.  Looks like 28 of the 100 reserved blocks have been used - is that what #180 means (I have doubts, since one is raw numbers and the other is a percentage)?
#251 needs to be looked up, just to be certain.

I have a different model Micron. It doesn't have the same attributes.

If nobody said this already, be certain to update the firmware for the SSD.
Sorry I'm not any more help.

---

### Post by manmath on 2022-02-19
Thanks TheFu and others who stood by me this far!
This morning I replaced that SSD (it was still under warranty) with a new one at my local seller. Now no more error message. A little pain to undergo the install routine, but it was worth it. Boot time has improved drastically. But one gripe that we could not know the exact reason behind those error message. Here's systemd report, also suggest if I can tweak any service/daemon to still improve the boot time (I know I'm being greedy):
```

manmath@manmath:~$ systemd-analyze 
Startup finished in 977ms (kernel) + 1.691s (userspace) = 2.669s 
graphical.target reached after 1.682s in userspace
manmath@manmath:~$ systemd-analyze blame | nl
     1  409ms e2scrub_reap.service
     2  221ms udisks2.service
     3  217ms dev-sda1.device
     4  147ms NetworkManager.service
     5   85ms wpa_supplicant.service
     6   84ms systemd-fsck@dev-disk-by\x2duuid-8135a85a\x2d30ae\x2d450a\x2dbc04\x2d213e960dc170.service
     7   73ms keyboard-setup.service
     8   73ms user@1000.service
     9   59ms systemd-udev-trigger.service
    10   52ms systemd-udevd.service
    11   46ms polkit.service
    12   45ms systemd-journald.service
    13   43ms lm-sensors.service
    14   37ms systemd-timesyncd.service
    15   36ms networking.service
    16   35ms alsa-restore.service
    17   33ms modprobe@drm.service
    18   33ms systemd-logind.service
    19   21ms systemd-tmpfiles-setup.service
    20   16ms systemd-sysusers.service
    21   16ms systemd-tmpfiles-setup-dev.service
    22   15ms modprobe@fuse.service
    23   14ms systemd-sysctl.service
    24   14ms systemd-remount-fs.service
    25   12ms dev-hugepages.mount
    26   12ms dev-mqueue.mount
    27   10ms nvi.service
    28    9ms modprobe@configfs.service
    29    9ms systemd-user-sessions.service
    30    9ms home-manmath-data.mount
    31    8ms systemd-update-utmp.service
    32    8ms systemd-modules-load.service
    33    8ms systemd-update-utmp-runlevel.service                                                                                                                                                               
    34    7ms kmod-static-nodes.service                                                                                                                                                                          
    35    7ms user-runtime-dir@1000.service                                                                                                                                                                      
    36    6ms systemd-rfkill.service                                                                                                                                                                             
    37    6ms systemd-journal-flush.service                                                                                                                                                                      
    38    3ms console-setup.service                                                                                                                                                                              
    39    3ms ifupdown-pre.service                                                                                                                                                                               
    40    3ms sys-kernel-config.mount                                                                                                                                                                            
    41    2ms sys-fs-fuse-connections.mount 
```

What is e2scrub_reap.service? Should I disable that?

---

### Post by mIk3_08 on 2022-02-19
> **manmath said:**
> Thanks TheFu and others who stood by me this far!
This morning I replaced that SSD (it was still under warranty) with a new one at my local seller. Now no more error message. A little pain to undergo the install routine, but it was worth it. Boot time has improved drastically. But one gripe that we could not know the exact reason behind those error message. Here's systemd report, also suggest if I can tweak any service/daemon to still improve the boot time (I know I'm being greedy):
```

manmath@manmath:~$ systemd-analyze 
Startup finished in 977ms (kernel) + 1.691s (userspace) = 2.669s 
graphical.target reached after 1.682s in userspace
manmath@manmath:~$ systemd-analyze blame | nl
     1  409ms e2scrub_reap.service
     2  221ms udisks2.service
     3  217ms dev-sda1.device
     4  147ms NetworkManager.service
     5   85ms wpa_supplicant.service
     6   84ms systemd-fsck@dev-disk-by\x2duuid-8135a85a\x2d30ae\x2d450a\x2dbc04\x2d213e960dc170.service
     7   73ms keyboard-setup.service
     8   73ms user@1000.service
     9   59ms systemd-udev-trigger.service
    10   52ms systemd-udevd.service
    11   46ms polkit.service
    12   45ms systemd-journald.service
    13   43ms lm-sensors.service
    14   37ms systemd-timesyncd.service
    15   36ms networking.service
    16   35ms alsa-restore.service
    17   33ms modprobe@drm.service
    18   33ms systemd-logind.service
    19   21ms systemd-tmpfiles-setup.service
    20   16ms systemd-sysusers.service
    21   16ms systemd-tmpfiles-setup-dev.service
    22   15ms modprobe@fuse.service
    23   14ms systemd-sysctl.service
    24   14ms systemd-remount-fs.service
    25   12ms dev-hugepages.mount
    26   12ms dev-mqueue.mount
    27   10ms nvi.service
    28    9ms modprobe@configfs.service
    29    9ms systemd-user-sessions.service
    30    9ms home-manmath-data.mount
    31    8ms systemd-update-utmp.service
    32    8ms systemd-modules-load.service
    33    8ms systemd-update-utmp-runlevel.service                                                                                                                                                               
    34    7ms kmod-static-nodes.service                                                                                                                                                                          
    35    7ms user-runtime-dir@1000.service                                                                                                                                                                      
    36    6ms systemd-rfkill.service                                                                                                                                                                             
    37    6ms systemd-journal-flush.service                                                                                                                                                                      
    38    3ms console-setup.service                                                                                                                                                                              
    39    3ms ifupdown-pre.service                                                                                                                                                                               
    40    3ms sys-kernel-config.mount                                                                                                                                                                            
    41    2ms sys-fs-fuse-connections.mount 
```

What is e2scrub_reap.service? Should I disable that?
I have done a little bit research about this they say that this is tied to the lvm side this is still under discussion of the systemd folks so, if you remove this service better have the understanding on it and should have take the risk.
Good luck and cheers.

---

### Post by manmath on 2022-02-19
Thanks Mike! I don't have LVM or raid, so I disabled the service (**suggest me its pros and cons if you get to know**). Now booting blazing fast. I turn on the start button and boom, the desktop is ready:
```
manmath@manmath:~$ systemd-analyze 
Startup finished in 957ms (kernel) + 931ms (userspace) = 1.888s 
graphical.target reached after 921ms in userspace
```

---

### Post by mIk3_08 on 2022-02-19
> **manmath said:**
> Thanks Mike! I don't have LVM or raid, so I disabled the service (**suggest me its pros and cons if you get to know**). Now booting blazing fast. I turn on the start button and boom, the desktop is ready:
```
manmath@manmath:~$ systemd-analyze 
Startup finished in 957ms (kernel) + 931ms (userspace) = 1.888s 
graphical.target reached after 921ms in userspace
``` nice, nice... Thanks for sharing your thoughts. This can also help to others that has same issue like this. Regards.

---

### Post by manmath on 2022-02-20
My pleasure, thanks!

---


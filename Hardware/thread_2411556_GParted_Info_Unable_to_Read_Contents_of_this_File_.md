---
title: "GParted Info: Unable to Read Contents of this File System!"
date: 2019-01-31
forum: Hardware
---

### Post by webmanoffesto on 2019-01-31
I have a drive that's giving me problems. I used a script to mount all partitions. Then I went to GParted to confirm that it's mounted. I saw an "info" button so I clicked it and it gave me this?
Do you have recommendations on how I should proceed or should I just consider it a failed drive and install a new one?
[IMG]https://i.imgur.com/7yRpUTDt.png[/IMG][https://i.ibb.co/KbqgSK1/GParted-sdb1-Unable-to-read-contents-2019-01-31-16-57-10.png](https://i.ibb.co/KbqgSK1/GParted-sdb1-Unable-to-read-contents-2019-01-31-16-57-10.png)

Then I went to Disks / Check File System but it said 
Error unmounting /dev/sdb1: umount failed: invalid argument (udisks-error-quark,0)
[IMG]https://i.imgur.com/cSRZB85t.png[/IMG][https://i.imgur.com/cSRZB85.png](https://i.imgur.com/cSRZB85.png)

---

### Post by TheFu on 2019-01-31
gparted can't read LVM information.  That could be what you are seeing.  

I don't use GUI tools for disk management.  If you could post the commands and output from :
```
sudo fdisks -l
df -hT

``` using code tags like I've done, maybe we can help?

And if you can, the test results from **smartctl** on each disk would be helpful too.

---

### Post by webmanoffesto on 2019-02-01
> **TheFu said:**
> I don't use GUI tools for disk management.  If you could post the commands and output from :
```
sudo fdisks -l
df -hT

```
And if you can, the test results from **smartctl** on each disk would be helpful too.

I installed and tried to run smartctl but it didn't work. Because the drives were mounted? Or because they weren't mounted?

```


ubuntu@ubuntu:~/bin$ chmod +x mount.all.sdb.sh
ubuntu@ubuntu:~/bin$ ./mount.all.sdb.sh
Hello, World!
mount: /mnt/boot/efi: mount point does not exist.
sudo mount -B /dev /mnt/dev
sudo mount -B /dev/pts /mnt/dev/pts
sudo mount -B /proc /mnt/proc
sudo mount -B /sys /mnt/sys
sudo mount -B /run /mnt/run
ubuntu@ubuntu:~/bin$ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1953349632 bytes, 3815136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x663eb4c4

Device       Boot   Start     End Sectors  Size Id Type
/dev/loop0p1 *          0 3815135 3815136  1.8G  0 Empty
/dev/loop0p2      3737268 3741939    4672  2.3M ef EFI (FAT-12/16/32)


Disk /dev/loop1: 1.8 GiB, 1864450048 bytes, 3641504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A5A2DC23-580C-4A05-B4C2-946278BF5096

Device        Start      End  Sectors  Size Type
/dev/sdb1      2048 11720797 11718750  5.6G Linux filesystem
/dev/sdb2  11722752 62531583 50808832 24.2G Linux filesystem


Disk /dev/sdc: 29.8 GiB, 32015679488 bytes, 62530624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x686a6515

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sdc1  *        2048 60434431 60432384 28.8G  b W95 FAT32
/dev/sdc2       60434432 62529535  2095104 1023M 83 Linux


Disk /dev/loop8: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
ubuntu@ubuntu:~/bin$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     787M  1.7M  785M   1% /run
/dev/sdc1      vfat       29G   18G   12G  61% /isodevice
/dev/loop0     iso9660   1.9G  1.9G     0 100% /cdrom
/dev/loop1     squashfs  1.8G  1.8G     0 100% /rofs
/cow           overlay   3.9G  466M  3.4G  12% /
tmpfs          tmpfs     3.9G   30M  3.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G   12M  3.9G   1% /tmp
tmpfs          tmpfs     787M   52K  787M   1% /run/user/999
/dev/loop2     squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop3     squashfs   35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop4     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop5     squashfs  2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop6     squashfs   13M   13M     0 100% /snap/gnome-characters/103
/dev/loop7     squashfs   15M   15M     0 100% /snap/gnome-logs/37
/dev/loop8     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
ubuntu@ubuntu:~/bin$ smartctl /dev/sdb1
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

Smartctl open device: /dev/sdb1 failed: Permission denied
ubuntu@ubuntu:~/bin$ umount /dev/sdb1
umount: /dev/sdb1: not mounted.
ubuntu@ubuntu:~/bin$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted.
ubuntu@ubuntu:~/bin$ 




```

---

### Post by TheFu on 2019-02-01
**smartctl** requires sudo. It works on the entire disk, but only does destructive actions if you specifically tell it to. SMART must be enabled in the BIOS for it to work. Some low-end systems don't have the SMART toggle in the BIOS, but most do.  I can't think of any known downside to having it enabled.

Generally, SMART data is gathered by running tests - long or short.  Then a few minutes to hours later, we can ask for the results of those tests.
```
sudo smartctl -t short /dev/sda
# wait 3 - 5 min
sudo smartctl -A /dev/sda
```
Sometimes, device options are necessary. I have a USB3 external array that needs to be told the device type or SMART stuff doesn't work.  Internal SATA disks have never shown that issue, that I've seen.

Sorry I said fdisks.  I use _tab-completion_, so knowing the exact name isn't something I need to know.  Basically, if you are typing more than 3 characters at a time, then you aren't been efficient on the shell.

All the 'loop' devices aren't needed. They aren't real storage. It is an artifact of the new snap package system.  No need to ever show loop devices in fdisk/parted or df output, unless you are specifically working a snap issue.

Anyways, looks like /dev/sda is the problem drive.  Until we see the SMART data, I'd lean towards 
* failing disk
* corrupted MBR/GPT partition table
* bad cable
* bad SATA port
* failing controller (either disk or HBA)

---

### Post by webmanoffesto on 2019-02-01
Some smartctl output
I didn't see output of the first smartctl command so I searched online and ran some other smartctl commands

```
ubuntu@ubuntu:~/bin$ sudo smartctl -t short /dev/sdb
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Fri Feb  1 20:37:57 2019

Use smartctl -X to abort test.
ubuntu@ubuntu:~/bin$ sudo smartctl --capabilities /dev/sdb
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (   57) seconds.
Offline data collection
capabilities:              (0x71) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0002)    Does not save SMART data before
                    entering power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (   1) minutes.
Conveyance self-test routine
recommended polling time:      (   1) minutes.

ubuntu@ubuntu:~/bin$ sudo smartctl --attributes /dev/sdb
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   100   100   000    Old_age   Offline      -       0
  5 Reallocated_Sector_Ct   0x0000   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0000   100   100   000    Old_age   Offline      -       4008
 12 Power_Cycle_Count       0x0000   100   100   000    Old_age   Offline      -       185
160 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0
161 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       56
163 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       12
164 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       218108
165 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       264
166 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       161
167 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       211
168 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       3000
169 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       93
175 Program_Fail_Count_Chip 0x0000   100   100   000    Old_age   Offline      -       0
176 Erase_Fail_Count_Chip   0x0000   100   100   000    Old_age   Offline      -       0
177 Wear_Leveling_Count     0x0000   100   100   050    Old_age   Offline      -       1339
178 Used_Rsvd_Blk_Cnt_Chip  0x0000   100   100   000    Old_age   Offline      -       0
181 Program_Fail_Cnt_Total  0x0000   100   100   000    Old_age   Offline      -       0
182 Erase_Fail_Count_Total  0x0000   100   100   000    Old_age   Offline      -       0
192 Power-Off_Retract_Count 0x0000   100   100   000    Old_age   Offline      -       50
194 Temperature_Celsius     0x0000   100   100   000    Old_age   Offline      -       37
195 Hardware_ECC_Recovered  0x0000   100   100   000    Old_age   Offline      -       25
196 Reallocated_Event_Count 0x0000   100   100   016    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0000   100   100   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0000   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0000   100   100   050    Old_age   Offline      -       0
232 Available_Reservd_Space 0x0000   100   100   000    Old_age   Offline      -       100
241 Total_LBAs_Written      0x0000   100   100   000    Old_age   Offline      -       106486
242 Total_LBAs_Read         0x0000   100   100   000    Old_age   Offline      -       171373
245 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       218108

ubuntu@ubuntu:~/bin$ 
ubuntu@ubuntu:~/bin$ sudo smartctl --test=short /dev/sdb
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Fri Feb  1 21:12:07 2019

Use smartctl -X to abort test.
ubuntu@ubuntu:~/bin$ sudo smartctl --capabilities /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (17760) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 199) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

ubuntu@ubuntu:~/bin$ 


```

---

### Post by oldfred on 2019-02-01
You can exclude snaps in partition list:

       exclude snaps
lsblk -af |grep -sv loop 

I have deleted all my snaps, so cannot test above, but posted previously.

---

### Post by TheFu on 2019-02-02
We need to see the  **sudo smartctl -A /dev/sda** output.

So, if sda is the problem disk and SMART data isn't working for it, and you've addressed the possible issues in my list above, and sda still doesn't work, there is only 1 thing left. sda is busted and needs to be swapped with a working, or more compatible, HDD.

Showing sdb output is good in that we see a working storage device, but it has nothing to do with sda's issues.  At least as far as I can tell.  You might swap the SATA cable from sdb with sda's, assuming the sdb is connected via SATA.

---

### Post by webmanoffesto on 2019-02-02
> **TheFu said:**
> We need to see the  **sudo smartctl -A /dev/sda** output.

```

$ sudo smartctl -A /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   181   180   021    Pre-fail  Always       -       1908
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       124
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       10341
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       105
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       85
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       72
194 Temperature_Celsius     0x0022   112   097   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

ubuntu@ubuntu:~$ sudo smartctl -A /dev/sdb
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   100   100   000    Old_age   Offline      -       0
  5 Reallocated_Sector_Ct   0x0000   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0000   100   100   000    Old_age   Offline      -       4025
 12 Power_Cycle_Count       0x0000   100   100   000    Old_age   Offline      -       187
160 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0
161 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       56
163 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       12
164 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       218108
165 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       264
166 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       161
167 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       211
168 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       3000
169 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       93
175 Program_Fail_Count_Chip 0x0000   100   100   000    Old_age   Offline      -       0
176 Erase_Fail_Count_Chip   0x0000   100   100   000    Old_age   Offline      -       0
177 Wear_Leveling_Count     0x0000   100   100   050    Old_age   Offline      -       1339
178 Used_Rsvd_Blk_Cnt_Chip  0x0000   100   100   000    Old_age   Offline      -       0
181 Program_Fail_Cnt_Total  0x0000   100   100   000    Old_age   Offline      -       0
182 Erase_Fail_Count_Total  0x0000   100   100   000    Old_age   Offline      -       0
192 Power-Off_Retract_Count 0x0000   100   100   000    Old_age   Offline      -       50
194 Temperature_Celsius     0x0000   100   100   000    Old_age   Offline      -       30
195 Hardware_ECC_Recovered  0x0000   100   100   000    Old_age   Offline      -       25
196 Reallocated_Event_Count 0x0000   100   100   016    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0000   100   100   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0000   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0000   100   100   050    Old_age   Offline      -       0
232 Available_Reservd_Space 0x0000   100   100   000    Old_age   Offline      -       100
241 Total_LBAs_Written      0x0000   100   100   000    Old_age   Offline      -       106486
242 Total_LBAs_Read         0x0000   100   100   000    Old_age   Offline      -       171374
245 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       218108

$ sudo smartctl -A /dev/sdb
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   100   100   000    Old_age   Offline      -       0
  5 Reallocated_Sector_Ct   0x0000   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0000   100   100   000    Old_age   Offline      -       4025
 12 Power_Cycle_Count       0x0000   100   100   000    Old_age   Offline      -       187
160 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0
161 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       56
163 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       12
164 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       218108
165 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       264
166 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       161
167 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       211
168 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       3000
169 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       93
175 Program_Fail_Count_Chip 0x0000   100   100   000    Old_age   Offline      -       0
176 Erase_Fail_Count_Chip   0x0000   100   100   000    Old_age   Offline      -       0
177 Wear_Leveling_Count     0x0000   100   100   050    Old_age   Offline      -       1339
178 Used_Rsvd_Blk_Cnt_Chip  0x0000   100   100   000    Old_age   Offline      -       0
181 Program_Fail_Cnt_Total  0x0000   100   100   000    Old_age   Offline      -       0
182 Erase_Fail_Count_Total  0x0000   100   100   000    Old_age   Offline      -       0
192 Power-Off_Retract_Count 0x0000   100   100   000    Old_age   Offline      -       50
194 Temperature_Celsius     0x0000   100   100   000    Old_age   Offline      -       30
195 Hardware_ECC_Recovered  0x0000   100   100   000    Old_age   Offline      -       25
196 Reallocated_Event_Count 0x0000   100   100   016    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0000   100   100   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0000   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0000   100   100   050    Old_age   Offline      -       0
232 Available_Reservd_Space 0x0000   100   100   000    Old_age   Offline      -       100
241 Total_LBAs_Written      0x0000   100   100   000    Old_age   Offline      -       106486
242 Total_LBAs_Read         0x0000   100   100   000    Old_age   Offline      -       171374
245 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       218108




```

---

### Post by TheFu on 2019-02-02
Ah ... I went back and looked at the OP again.  You only claim that sdb is the issue.  Do the drives move around on you, changing device names?  Sometimes that can happen, which is why Linux uses UUIDs in the fstab for mounts.

So - according to SMART, sda is fine, just old.  I would keep using it, but definitely have good backups. That goes for any storage, so nothing new.

If this is still the result for fdisk -l /dev/sda```

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```
and nothing more, then I'd create a new gpt partition table, add a primary partition and start using the disk. I'd use **gparted** on a desktop to do that. It has to run with sudo, so **sudo -H gparted** is the command.

/dev/sdb looks fine too, except the physical connect seems off a little due to ECC corrections.  I'd swap the cable, assuming it has a cable.  If it is NVMe, then the slot it is using or some of the pins don't have a good electrical connection.

```
Device        Start      End  Sectors  Size Type
/dev/sdb1      2048 11720797 11718750  5.6G Linux filesystem
/dev/sdb2  11722752 62531583 50808832 24.2G Linux filesystem
```
How do the 2 partitions mount when you manually mount them?

If **sudo lsblk |egrep -v loop** comes back as you expect, try:

```
sudo mkdir /mnt/1 /mnt/2
sudo mount /dev/sdb1  /mnt/1
sudo mount /dev/sdb2  /mnt/2
df -hT |grep /mnt
```

Does that work?  All the files there and accessible based on the file and directory permissions?

I got fixated on sda due to the fdisk output. Sorry if that wasn't anything you cared about.  sdb looked mostly fine, but SMART misses failed disks about 22% of the time according to Backblaze.  You can find their *drive reliability reports* online.  Trying to use a GUI to mount disks isn't anything I've done.  I've seen others here who I respect say to avoid doing that - using a GUI to mount local disks.

---


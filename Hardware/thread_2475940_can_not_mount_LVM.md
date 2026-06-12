---
title: "can not mount LVM"
date: 2022-06-12
forum: Hardware
---

### Post by Raymond Day on 2022-06-12
I was trying to copy a 2 drive 1TB each so 2TB LVM to a 2 drive 2TB each so 4TB.

But it locked up after a long time.

When I went to reboot it it says can't find the LVM.

Put it on another server.

When I try and mount it looks like this.

root@server:~# mount /dev/mapper/SG30-sg30--2TB /media/sg30
mount: /media/sg30: wrong fs type, bad option, bad superblock on /dev/mapper/SG30-sg30--2TB, missing codepage or helper program, or other error.
root@server:~#

Is there a way to fix this so I can mount it?

-Raymond Day

---

### Post by TheFu on 2022-06-13
Did you run an fsck on the device that holds the file system?

If you need more specific answers, we need exact data.  Provide
```
sudo lvs
sudo vgs
# and perhaps
lsblk -e 7 -o name,size,type,fstype,mountpoint

```

Use code tags, so the output lines up. Otherwise it is too hard to decipher.

---

### Post by Raymond Day on 2022-06-13
Yes it says clean.

root@server:~# fsck /dev/mapper/SG30-sg30--2TB
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/mapper/SG30-sg30--2TB: clean, 11/60960256 files, 479110/61014016 blocks
root@server:~# mount /dev/mapper/SG30-sg30--2TB /media/sg30
mount: /media/sg30: wrong fs type, bad option, bad superblock on /dev/mapper/SG30-sg30--2TB, missing codepage or helper program, or other error.
root@server:~#

-Raymond Day

---

### Post by TheFu on 2022-06-13
Looks like you need to specify the file system type on the mount options.

The lsblk command asked for above should provide that information.

---

### Post by Raymond Day on 2022-06-14
lsblk show this:

sds                                    65:32   0 931.5G  0 disk
&#9500;&#9472;sds1                                 65:33   0   487M  0 part
&#9500;&#9472;sds2                                 65:34   0     1K  0 part
&#9492;&#9472;sds5                                 65:37   0   931G  0 part
  &#9492;&#9472;SG30-sg30--2TB                    253:6    0   1.8T  0 lvm

The Partitions looks like like this:

sds1 boot
sds2 is not LVM but sds5 is in the sds2 Partition they are about the same size. The 2nd SSD is one bit Partition sds5 to SG30-sg30--2TB and it is 2TB because it has 2 SSD 1TB.

-Raymond Day

---

### Post by Raymond Day on 2022-06-14
I can mount the boot but not the 2nd partition it should be a big same size about as the LVM partition as the 3rd partition because the 2nd partition has the 3rd partition inside it.

Here is command to just mount it and not the LVM.

It did work on the boot partition can mount that.

root@server:~# mount /dev/sds1 /media/sg30/
root@server:~# mount /dev/sds2 /media/sg30-2/
NTFS signature is missing.
Failed to mount '/dev/sds2': Invalid argument
The device '/dev/sds2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@server:~# fsck /dev/sds2
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sds2
Could this be a zero-length partition?
root@server:~#

-Raymond Day

---

### Post by TheFu on 2022-06-14
Please run the commands in post #2 above, with the options requested,  post the results AND use forum code tags.

This shouldn't be so hard to get the requested information.

I seriously doubt "sds1" is correct. Do you really have 15+ storage devices connected to the system?

---

### Post by Raymond Day on 2022-06-14
Just ran them commands and it comes back like this. I have other LVM on it too.

```

root@server:~# lvs
  LV                  VG              Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  12TB+8TB            12TB+8TB        -wi-ao---- 18.00t
  12and8TB-backup     12TB+8TB-backup -wi-ao---- 18.00t
**  sg30-2TB            SG30_2TB        -wi-a----- <1.82t**
  WP-4TB-2-SSD-sticks WP-4TB          -wi-ao---- <3.64t
root@server:~# vgs
  VG              #PV #LV #SN Attr   VSize  VFree
  12TB+8TB          2   1   0 wz--n- 18.19t 196.00g
  12TB+8TB-backup   2   1   0 wz--n- 18.19t 195.96g
**  SG30_2TB          2   1   0 wz--n- <1.82t 556.00m**
  WP-4TB            2   1   0 wz--n- <3.64t  32.00m
root@server:~# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                                    SIZE TYPE FSTYPE      MOUNTPOINT
sda                                     1.8T disk
&#9492;&#9472;sda1                                  1.8T part LVM2_member
  &#9492;&#9472;WP--4TB-WP--4TB--2--SSD--sticks     3.7T lvm  ext4        /media/WP-4TB
sdb                                     3.7T disk
&#9500;&#9472;sdb1                                  512M part vfat
&#9492;&#9472;sdb2                                  3.7T part ext4        /
sdc                                     9.1T disk
&#9492;&#9472;sdc1                                  9.1T part ext4        /media/WD-10TB
sdd                                     2.7T disk
&#9492;&#9472;sdd1                                  2.7T part ext4        /media/3TB_USB
sde                                     7.3T disk
&#9492;&#9472;sde1                                  7.3T part LVM2_member
  &#9492;&#9472;12TB+8TB--backup-12and8TB--backup    18T lvm  ext4        /media/12+8TB-backup
sdf                                     2.7T disk
&#9492;&#9472;sdf1                                  2.7T part ext4        /media/3TB-Black-laptop-size
sdg                                    10.9T disk
&#9492;&#9472;sdg1                                 10.9T part LVM2_member
  &#9492;&#9472;12TB+8TB--backup-12and8TB--backup    18T lvm  ext4        /media/12+8TB-backup
sdh                                     1.8T disk swap        [SWAP]
sdi                                   931.5G disk
&#9492;&#9472;sdi1                                931.5G part ext4        /media/WD-1TB
sdj                                   465.8G disk
&#9492;&#9472;sdj1                                465.8G part ext4        /media/500GB-blue-ssd
sdk                                     9.1T disk
&#9492;&#9472;sdk1                                  9.1T part ext4        /media/WD-10TB-4
sdl                                     7.3T disk LVM2_member
&#9492;&#9472;12TB+8TB-12TB+8TB                      18T lvm  ext4        /media/12TB+8TB
sdm                                   465.8G disk
&#9492;&#9472;sdm1                                465.8G part ext4        /media/500GB-3D-NAND
[B]sdn                                   931.5G disk
&#9500;&#9472;sdn1                                  487M part ext2
&#9500;&#9472;sdn2                                    1K part
&#9492;&#9472;sdn5                                  931G part LVM2_member
  &#9492;&#9472;SG30_2TB-sg30--2TB                  1.8T lvm  ext2
sdo                                   931.5G disk LVM2_member
&#9492;&#9472;SG30_2TB-sg30--2TB                    1.8T lvm  ext2[/B]
sdp                                   115.7G disk
&#9492;&#9472;sdp1                                115.7G part ext4        /media/PiDrive-USB128GB
sdq                                     9.1T disk
&#9492;&#9472;sdq1                                  9.1T part ext4        /media/WD-10TB-3
sdr                                    10.9T disk LVM2_member
&#9492;&#9472;12TB+8TB-12TB+8TB                      18T lvm  ext4        /media/12TB+8TB
sds                                     9.1T disk
&#9492;&#9472;sds1                                  9.1T part ext4        /media/WD-10TB-2
sdt                                    18.2T disk
&#9492;&#9472;sdt1                                 18.2T part ext4        /media/WD-20TB
nvme0n1                                 1.8T disk LVM2_member
&#9492;&#9472;WP--4TB-WP--4TB--2--SSD--sticks       3.7T lvm  ext4        /media/WP-4TB
root@server:~#

```

So the part looking for on the last command is in bold text.

Hope this helps.

Still if I try and mount it just get this:

root@server:~# mount /dev/SG30_2TB/sg30-2TB /media/sg30-lvm/
mount: /media/sg30-lvm: wrong fs type, bad option, bad superblock on /dev/mapper/SG30_2TB-sg30--2TB, missing codepage or helper program, or other error.
root@server:~#

-Raymond Day

---

### Post by TheFu on 2022-06-14
forum code tags?  Too hard to read as is.
Code Tags: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by Raymond Day on 2022-06-14
This my help. I reload this on the same it locked up on only on 2 new SSD's but 2TB each to LVM = 4TB looks like one 4TB drive but using two 2TB drives.

```

root@sg30:~# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                 SIZE TYPE FSTYPE      MOUNTPOINT
sda                  1.8T disk
&#9500;&#9472;sda1               487M part ext2        /boot
&#9500;&#9472;sda2                 1K part
&#9492;&#9472;sda5               1.8T part LVM2_member
  &#9500;&#9472;sg30--vg-root    3.6T lvm  ext4        /
  &#9492;&#9472;sg30--vg-swap_1  976M lvm  swap        [SWAP]
sdb                  1.8T disk LVM2_member
&#9492;&#9472;sg30--vg-root      3.6T lvm  ext4        /
root@sg30:~#

```

This boots and works good. I guess it should look some what like that on the other server. That trying to just mount it on.

I used Debian on the sg30 and when install it was Debian 10 I think and it had all the updates when it locked up. This new on installed Debian 11 server.

-Raymond Day

---

### Post by TheFu on 2022-06-14
```
sudo mkdir /mnt/temp
sudo mount -t ext4   /dev/SG30_2TB/sg30-2TB /mnt/temp
```


If that doesn't work, and you've run ```
sudo fsck -y   /dev/SG30_2TB/sg30-2TB
``` , then I'd start comparing versions of LVM to see if the Ubuntu one and Debian one are the same/compatible.  I don't know if this is an issue. I've never mixed OSes with LVM.

I don't  mount permanent storage under /media for a number of reasons.  And I wouldn't leave this mount under /mnt/ either. Both of those directories are for specific uses.  /mnt is for temporary stuff and /media/ is for non-permanent mounts - typically for optical media.

---

### Post by Raymond Day on 2022-06-15
I did this what you ask for:

```

root@server:~# mkdir /mnt/temp
root@server:~# mount -t ext4   /dev/SG30_2TB/sg30-2TB /mnt/temp
mount: /mnt/temp: wrong fs type, bad option, bad superblock on /dev/mapper/SG30_2TB-sg30--2TB, missing codepage or helper program, or other error.
root@server:~# fsck -y   /dev/SG30_2TB/sg30-2TB
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/mapper/SG30_2TB-sg30--2TB: clean, 11/60960256 files, 479110/61014016 blocks
root@server:~#

```

But nothing is there:

```

root@server:~# cd /mnt/temp
root@server:/mnt/temp# ll
total 8
drwxr-xr-x 2 root root 4096 Jun 15 00:09 ./
drwxr-xr-x 3 root root 4096 Jun 15 00:09 ../
root@server:/mnt/temp#

```

So it did not work.

-Raymond Day

---

### Post by TheFu on 2022-06-15
Well, crap. 

I'm back to the LVM versions being different. Have you checked that?

The fact that one of the LVs is in a VG that is in a partition and the other is in a VG that was put on the whole disk could be an issue.  I'd not seen that before.  The best practice for LVM is to always use partitions for PV/VGs.  I can't say if this **is** the issue, just that it seems funny and could be the problem.  Can you backup everything in the LV, then recreate the VG under a partition?

Ref:
```
sdb                  1.8T disk LVM2_member
&#9492;&#9472;sg30--vg-root      3.6T lvm  ext4        /
```

My last guess, and it is reaching, is that one of the drives is failing. Check the SMART data for both.

---

### Post by Raymond Day on 2022-06-15
They are 2 1TB SSD's so I am sure not failing.

Something went wrong when it was running and while it was running wanted to copy the LVM to another LVM with 2 SSD there were 2TB each. But it locked up and on a reboot could not boot any more. So this is on another server to see it but can not mount it. I guess that's why it could not boot any more.

So something when it copied messed it up. Should of copied it with out it running.

That code you showed is on a working one I reloaded fresh on the same system it the old one locked up on.

-Raymond Day

---

### Post by TheFu on 2022-06-15
SSDs fail.  I've had a few fail and know that enterprise SSDs fail around 0.5% in the first month.  SSDs aren't perfect. There are some with initial flaws.

There are a few warnings around using fsck incorrectly with LVM.  Never run it when the file system is mounted. Always use the LV device, not the partition or VG. Stuff like that.
There are multiple ways to move data in LVM ... or were you using rsync?   I've used pvmove to migrate off a HDD onto an SSD while the system was running. Worked fine.  I've not tried to move data that was split between multiple storage devices while inside LVM.   

About 20 yrs ago, I lost 80% of my data when using concatenated LVM into a single LV that crossed 3 partitions. 1 disk failed.  I probably have those 3 disks on a shelf somewhere and should be able to get 2/3rd of the data back now that my skills are greater.  All my backups are file-based and limited to 4TB LVs/partitions.

---

### Post by Raymond Day on 2022-06-15
Wow I never had a SSD fail on me. No moving parts. If you wright to them on the same spot for about a million times can fail that spot then. But if just store data should last a long time and not change the date.

Off topic some.

Still can't mount this LVM nothing helps.

-Raymond Day

---

### Post by TheFu on 2022-06-15
> **Raymond Day said:**
> Wow I never had a SSD fail on me. No moving parts. If you wright to them on the same spot for about a million times can fail that spot then. But if just store data should last a long time and not change the date.

Off topic some.

Still can't mount this LVM nothing helps.

-Raymond Day

Did you look at the SMART data for both SSDs?  It is a waste of time to try to make something that has failed to work. Right?  Sure, it is unlikely, but at some point, the unlikely answer is all we have left.  

Did you setup the PV/VG on the device under a partition yet?

Did you check the LVM versions between the Ubuntu release and the Debian release?

We cannot read minds. If you don't tell us, we don't know and just think you are ignoring the ideas.

---

### Post by Raymond Day on 2022-06-15
Ok tested the smart and here how it shows it. I guess there my be some other smartctl command to show more or is this good?

```

root@server:/mnt/temp# smartctl -c /dev/sdn
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-117-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (    0) seconds.
Offline data collection
capabilities:                    (0x11) SMART execute Offline immediate.
                                        No Auto Offline data collection support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  10) minutes.

root@server:/mnt/temp# smartctl -c /dev/sdo
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-117-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (    0) seconds.
Offline data collection
capabilities:                    (0x11) SMART execute Offline immediate.
                                        No Auto Offline data collection support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  10) minutes.

root@server:/mnt/temp#

```

Thank you.

-Raymond Day

---

### Post by Raymond Day on 2022-06-15
Did the long test on them and waited about 10 min.

Got back this it says "Completed without error" But 00% so maybe got to wait longer not sure. But this is what got back:

```

root@server:/mnt/temp# smartctl -l selftest /dev/sdn
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-117-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%         0         -

root@server:/mnt/temp# smartctl -l selftest /dev/sdo
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-117-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%         0         -

root@server:/mnt/temp#

```

-Raymond Day

---

### Post by TheFu on 2022-06-15
There are 3 steps to using smartctl.

a) Run the test.  -t long or -t short    
b) Wait for that to complete. With SSDs, it is very fast.
c) Run a report.   -a is the option.

Some controllers/storage combinations require extra options to specify the controller, connection type, or drive type.  There should be an error if the defaults don't work.  The extra option is needed for both the test and the report.   NVMe reports tend to be less great.  

I run short tests weekly, automatically, on all storage here.  Monthly, I run a long test (if I don't forget).  The reports are saved into files and retained for 6 months.  With SMART data, seeing changes over time is where the greatest value happens.  Use a diff too to see the changes easily. Error counts and temperatures above the allowed range need to be monitored for an SSD.  

For HDDs, there are many more parameters. Look for anything with count, error, or relocated in the parameter name. Use the raw values, not the dumbed down value/worst, which seem to be useless.

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0

```
The raw values are useful. All is fine, but the 100/100 for the VALUE means nothing.
There's a way to setup smartctld to handle all of this cleaner. I'm old and just use cron.

Lots of reports here.
```
smart.2022-03-21.sdd      smart.2022-04-18.sde      smart.2022-05-09.sdf      smart.2022-06-06.sdg
smart.2022-03-21.sde      smart.2022-04-18.sdf      smart.2022-05-09.sdg      smart.2022-06-13.nvme0n1
smart.2022-03-21.sdf      smart.2022-04-18.sdg      smart.2022-05-16.nvme0n1  smart.2022-06-13.sda
smart.2022-03-21.sdg      smart.2022-04-25.nvme0n1  smart.2022-05-16.sda      smart.2022-06-13.sdb
smart.2022-03-28.nvme0n1  smart.2022-04-25.sda      smart.2022-05-16.sdb      smart.2022-06-13.sdc
smart.2022-03-28.sda      smart.2022-04-25.sdb      smart.2022-05-16.sdc      smart.2022-06-13.sdd
smart.2022-03-28.sdb      smart.2022-04-25.sdc      smart.2022-05-16.sdd      smart.2022-06-13.sde
smart.2022-03-28.sdc      smart.2022-04-25.sdd      smart.2022-05-16.sde      smart.2022-06-13.sdf
smart.2022-03-28.sdd      smart.2022-04-25.sde      smart.2022-05-16.sdf      smart.2022-06-13.sdg
smart.2022-03-28.sde      smart.2022-04-25.sdf      smart.2022-05-16.sdg
smart.2022-03-28.sdf      smart.2022-04-25.sdg      smart.2022-05-23.nvme0n1
```

---


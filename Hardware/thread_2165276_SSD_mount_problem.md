---
title: "SSD mount problem"
date: 2013-08-04
forum: Hardware
---

### Post by eliot3 on 2013-08-04
Hello ubuntu forum, I have a problem (this is my first post here, my apologies if I'm doing anything wrong!):

Ubuntu failed to boot this morning, there apparently is something wrong with my bootdisk. I booted from USB-Stick and got this message:
> Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
 missing codepage or helper program, or other error
 In some cases useful info is found in syslog - try
 dmesg | tail or so

Here's what else I could find out:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d6b97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   217761791   108879872   83  Linux
/dev/sda2       217763838   234440703     8338433    5  Extended
/dev/sda5       217763840   234440703     8338432   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcdc4cdc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312576704   156288321    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 3909 MB, 3909091328 bytes
121 heads, 62 sectors/track, 1017 cylinders, total 7634944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62     7629533     3814736    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ dmesg | tail
[  116.737343]         00 00 00 00 
[  116.737347] sd 6:0:0:0: [sda]  
[  116.737350] Add. Sense: Unrecovered read error - auto reallocate failed
[  116.737352] sd 6:0:0:0: [sda] CDB: 
[  116.737353] Read(10): 28 00 06 44 1d 18 00 00 f0 00
[  116.737361] end_request: I/O error, dev sda, sector 105127192
[  116.737380] ata7: EH complete
[  116.737427] JBD2: Failed to read block at offset 686
[  116.739603] JBD2: recovery failed
[  116.739608] EXT4-fs (sda1): error loading journal
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda
e2fsck 1.42 (29-Nov-2011)
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$
```

sda is the problem, 120GB SSD, sdb is an old 160GB IDE-disk with SATA-Adapter I use for data storage (I'm not even sure why it has a boot sector at all...), and sdc is the Bootstick.
System is Ubuntu 12.04 AMD64 on an ASRock H77 Pro4-M/Intel i5 Desktop.

---

### Post by Claus7 on 2013-08-04
Hello,

I think that your old drive complains. One thing that I would advice you is to use the same command (e2fsck), yet while your disk is unmounted:

sudo umount /dev/sda

and see what I can get.

If this is your boot drive then try the same command from an ubuntu cd.

Regards!

---

### Post by eliot3 on 2013-08-04
Hello Claus,
thanks for your reply, but that is not it. The old drive is sdb, it works normally. I can not mount or unmount sda, that is the SSD system disk. And I am trying all this from the clean ubuntu, booting from USB, since it is not possible to boot from hard disk.

---

### Post by oldfred on 2013-08-05
You do not run e2fsck on a drive but on a partition that is formatted with ext2, ext3 or ext4.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by eliot3 on 2013-08-05
Thanks oldfred! Here's what happened:
> ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
/dev/sda1: recovering journal
Error reading block 13140671 (Attempt to read block from filesystem resulted in short read).  

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

I redid it without -p, there was a motherload of errors, then rebooted (because the system told me there was no more user memory left), but now the SSD is gone completely, "sudo fdisk -l" gives me the Bootstick as sda, and the old storage disk as sdf, nothing else.
I should mention that I'm a complete noob with Linux, the diagnostics I quoted in my first post were just things I copied from various pages I found googling my error, I don't really know what I'm doing there. Is there a difference between a LiveCD and a USB Boot-Stick? (If so: I have a Ubuntu 10.10 32bit Live-CD lying around, can I use that, or is that too old to deal with SSDs usefully?)
Thanks again for the help!

---

### Post by oldfred on 2013-08-05
I have not seen that error, but if it says try again without -p try that. 
It may start to show lots of errors?

---

### Post by eliot3 on 2013-08-05
Thanks again, your reply and my edit happened simultaneously, it seems, please read above!

---

### Post by oldfred on 2013-08-05
I would not use any older Ubuntu. Best to use newest version so it has all the updates as the liveCD/DVD/Flash drive. USB boot drive could be a hard drive or a flash drive. But normally now live installers are flash drives as they are reuseable and now lower in cost, and CDs are not large enough for the newest version.

Does BIOS still show drive. If BIOS cannot see drive, then nothing we do with system will show it. And can you see it, then from Disks or Disk Utility and then click on drive and on right side it has Smart Status. That can run a lot of tests, but all I really know is whether is drive is good or not.

---

### Post by eliot3 on 2013-08-05
This is getting weirder and weirder - first the disk was gone from BIOS, then it didn't find the USB flashdisk. I pulled the AC plug, replugged, it found the disk again, could even access it, only I can't set it as boot device in BIOS, although fdisk shows it having a bootsector. I tried to backup the data while it was working, but in the middle of the backup tar aborted with an error, and the disk was gone again. Shut down, unplug, replug, disk is back, currently Disk Utility is running a self test.

edit: Extended test "completed OK", "Disk has a few bad sectors". But most of the attributes in the list show "Value: N/A" or "0" (including "231-Temperature", which I find hard to believe). And "Refresh SMART data" results in: "Error retrieving ATA SMART data: helper failed with exit code 1: Failed to check if disk /dev/sda is awake: Operation not supported"

"Check file system" gives: "File system is NOT clean"

Having no clue what is going on I suspect either the drive is shot, or  some SATA controller on the mainboard, or could it still be a software  problem? Or something completely different? How can I localize the  problem exactly?

edit2: Rebooted again, fiddled with the BIOS (actually, the UEFI I think this modern toy is called), and lo, it booted from the hard drive! Threw a heap of text at me, about lots of errors, asked me if it should correct them, I said yes, now it seems to work. No idea why, or how. I'll keep you posted what happens the next time I reboot... So, thanks for all the advice for now, I'd still appreciate some more hints about my questions above: Is it a hardware problem? Which part do I return to the dealer?

---

### Post by oldfred on 2013-08-05
Is this the SSD? 
Do you have AHCI on? And trim?
Using fstrim daily or discard in fstab?
       Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

What scheduler?

 cat /sys/block/sda/queue/scheduler

      
 Ubuntu now uses deadline as default I/O scheduler
[http://www.wilderssecurity.com/showthread.php?t=343415](http://www.wilderssecurity.com/showthread.php?t=343415)

 But per this noop may not now be best.
[http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)
noop may not be best scheduler for SSD, deadline may be better
[http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance](http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance)

---

### Post by eliot3 on 2013-08-06
Yes, booting now works from SSD again.
AHCI:
```
ubuntu@ubuntu:~$ dmesg | grep -i ahci
[    2.712423] ahci 0000:00:1f.2: version 3.0
[    2.712464] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    2.727578] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    2.727581] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    2.727586] ahci 0000:00:1f.2: setting latency timer to 64
[    2.767726] scsi0 : ahci
[    2.767766] scsi1 : ahci
[    2.767800] scsi2 : ahci
[    2.767833] scsi3 : ahci
[    2.767866] scsi4 : ahci
[    2.767897] scsi5 : ahci
[    2.768122] ahci 0000:04:00.0: irq 42 for MSI/MSI-X
[    2.768155] ahci: SSS flag set, parallel bus scan disabled
[    2.768207] ahci 0000:04:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    2.768209] ahci 0000:04:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    2.768370] scsi6 : ahci
[    2.768407] scsi7 : ahci
ubuntu@ubuntu:~$ 
```

Trim is on. I know the first link you posted, I did schedule a daily trim job following the instructions, but it didn't seem to work, so I did it manually (though more weekly than daily, I admit), planning to fix that problem one day when I get round to it. The drive is in fstab like this:
```
UUID=512e7b3d-6f0b-474c-9542-7910a1c9c8d1 /               ext4    noatime,nodiratime,discard,errors=remount-ro,defaults 0       1
```
Scheduler is deadline.

Here's more info on the drive:
```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     MKNSSDCR120GB
Serial Number:    MKN1708R000040505
LU WWN Device Id: 0 000120 000000000
Firmware Version: 506ABBF0
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ACS-2 revision 3
Local Time is:    Tue Aug  6 14:34:16 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  48) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x0021)    SCT Status supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   105   105   050    Pre-fail  Always       -       11074622
  5 Reallocated_Sector_Ct   0x0033   100   100   003    Pre-fail  Always       -       90
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       158939559756050
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       199
171 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       0
174 Unknown_Attribute       0x0030   000   000   000    Old_age   Offline      -       63
177 Wear_Leveling_Count     0x0000   000   000   000    Old_age   Offline      -       0
181 Program_Fail_Cnt_Total  0x0032   000   000   000    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   000   000   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   000   000   000    Old_age   Always       -       65535
190 Airflow_Temperature_Cel 0x0000   039   043   000    Old_age   Offline      -       39 (Min/Max 24/43)
194 Temperature_Celsius     0x0022   039   043   000    Old_age   Always       -       39 (Min/Max 24/43)
195 Hardware_ECC_Recovered  0x001c   120   120   000    Old_age   Offline      -       11074622
196 Reallocated_Event_Count 0x0033   100   100   003    Pre-fail  Always       -       90
201 Soft_Read_Error_Rate    0x001c   120   120   000    Old_age   Offline      -       11074622
204 Soft_ECC_Correction     0x001c   120   120   000    Old_age   Offline      -       11074622
230 Head_Amplitude          0x0013   100   100   000    Pre-fail  Always       -       100
231 Temperature_Celsius     0x0013   100   100   010    Pre-fail  Always       -       0
233 Media_Wearout_Indicator 0x0000   000   000   000    Old_age   Offline      -       286
234 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       219
241 Total_LBAs_Written      0x0032   000   000   000    Old_age   Always       -       219
242 Total_LBAs_Read         0x0032   000   000   000    Old_age   Always       -       396

SMART Error Log not supported
SMART Self-test Log not supported
Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```


There must still be some errors on the disk, because occasionally the system freezes, then comes alive again after some time, but the hard drive is gone. I guess it's because of the disk because it happens unopredictably in general, but every time I do something involving the whole SSD, like benchmark (in Disk Utility).
Edit again, tried booting from the Flashdisk again and run a benchmark on the drive while it's not the system disk. This time it didn't crash, but gave this error: "Error benchmarking: helper exited with exit code 1: Error reading 60792832 bytes at 49874952192 from /dev/sda: Input/output error"
Unmounted the disk, tried benchmark again, this time Disk Utility crashed.

---

### Post by oldfred on 2013-08-06
If running the discard in fstab, then you should not need the fstrim or vice-versa.

I do not think you need nodiratime as that is in noatime setting.

It does say passed and that is all I know about Smartctl, but you do seem to be having issues. Both smartctl and e2fsck have given errors.

---

### Post by eliot3 on 2013-08-26
Quick update: After several weeks of working normally, the drive terminally vanished from the UEFI without further warning signs. The return was accepted immediately, replacement is being shipped, I can only recommend to people with similar problems to bring the crap back right away... :(
This thread can be closed, I guess. Thanks to all for the suggestions!

---


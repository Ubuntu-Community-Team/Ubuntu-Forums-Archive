---
title: "New hard drive, filesystem drops out on idle periods"
date: 2010-02-10
forum: Hardware
---

### Post by Little Blue on 2010-02-10
Hi,

About a fortnight ago I replaced an ageing hard drive with a new one and reinstall my OS with a clean install of Karmic. Things have been running okish but this new harddrive is concerning me. For one its noisier than my old one.

More critically though only half an hour ago after I had just got back to my machine after about an hour leaving it idle whilst I do something and I found I couldn't run anything. Clicking icons in my panel returned a message that it couldn't find whatever, I couldn't even get into the terminal. Ctrl+Alt+F2 shifted me into a terminal session but I couldn't login; I'd enter my username but then it'd launch a series of traceback errors most of which seemed to reference ext4.

Upon forcing a restart I got dumped into a recovery session, received a few complaints along the lines of "/dev/sda1: Inodes that were part of a corrupted orphan linked list" and that "filesystem has errors: /" as well as "mount of filesystem failed". Eventually I was asked and able to manually run a fsck process.

Pass 1: Inodes that were part of a corrupted orphan linked list were found. Fix? y
Pass 2-4 seemed to go fine
Pass 5 gave me a lot of errors and queries to fix (which I did). "Block bitmap differences: -9606 -(10895733--10895736)" and "Free inodes count wrong for group #11 (8163, counted=8164)" as an example.

Summary was

```
/dev/sda1: Filesystem was modified
/dev/sda1: Reboot Linux
/dev/sda1: 213273/12283968 files (0.5% non-contiguous) 5927214/7710596 blocks
```

So what does this all mean? Is this new drive naff and going to fail on me any day now despite SMART in disk utilities saying it's healthy (I did notice that its spin-up time has increase from 229ms to 331ms since last week to now)? Is this more likely a filesystem error and so I need to reinstall?

Any advice would me much appreciated.

Thanks

Edit: Oh, this is the second time this has happened to me. The first was about a week ago, but it rebooted fine and for some reason didn't think much else of it.

---

### Post by Little Blue on 2010-02-11
ok, this happened again overnight... I'm really concerned now. Does anyone have anything to suggest?

---

### Post by Little Blue on 2010-02-12
and again! As I had a terminal window open before the filesystem dropped out I managed to make note of this:

```
ls /
ls: reading directory /: Input/output error

```

This is what dmesg says as well, though I've no idea if this is relevant to this issue...
```
[29472.184329]  [<c02627b9>] ? check_block_validity+0x99/0xa0
[29472.184334]  [<c02627b9>] ? check_block_validity+0x99/0xa0
[29472.184338]  [<c0145085>] warn_slowpath_null+0x15/0x20
[29472.184342]  [<c02627b9>] check_block_validity+0x99/0xa0
[29472.184346]  [<c0265aee>] ext4_get_blocks+0x1ae/0x200
[29472.184350]  [<c0265d38>] ext4_getblk+0x68/0x1c0
[29472.184354]  [<c0145085>] ? warn_slowpath_null+0x15/0x20
[29472.184359]  [<c03166d6>] ? put_dec+0x136/0x140
[29472.184363]  [<c012d28d>] ? kmap_atomic_prot+0xcd/0xf0
[29472.184368]  [<c026c792>] ext4_find_entry+0x322/0x410
[29472.184371]  [<c03169e7>] ? number+0x307/0x320
[29472.184379]  [<c0132f40>] ? __wake_up+0x40/0x50
[29472.184385]  [<c01f9c2e>] ? d_alloc+0x1e/0x190
[29472.184390]  [<c026c8bd>] ext4_lookup+0x3d/0x100
[29472.184396]  [<c0570fb8>] ? _spin_lock+0x8/0x10
[29472.184400]  [<c01f9d46>] ? d_alloc+0x136/0x190
[29472.184404]  [<c01effe7>] real_lookup+0xb7/0x110
[29472.184408]  [<c01f173d>] do_lookup+0x8d/0xb0
[29472.184411]  [<c01f20e4>] __link_path_walk+0x584/0xb90
[29472.184415]  [<c01f2881>] path_walk+0x41/0x90
[29472.184419]  [<c01f2921>] do_path_lookup+0x51/0x90
[29472.184422]  [<c01f343c>] user_path_at+0x3c/0x70
[29472.184429]  [<c01eba75>] vfs_fstatat+0x35/0x70
[29472.184433]  [<c01ebbbb>] vfs_stat+0x1b/0x20
[29472.184437]  [<c01ebbd4>] sys_stat64+0x14/0x30
[29472.184442]  [<c010336c>] syscall_call+0x7/0xb
[29472.184445] ---[ end trace 2daa8014f473e92f ]---

```

This time though it didn't boot into recovery mode to fsck the disk.

So I ask again, does anyone have any idea what's going on with my system as I don't and need more reliability than I am currenly getting...

---

### Post by Little Blue on 2010-02-12
I'm sorry to keep bringing this up, but its happened again: when I got home today the filesystem appeared to have unmounted itself again. In a terminal window I had left open before leaving this morning "ls /" reported nothing. Rebooting brought me into the recovery mode where I had to use fsck before / would mount.

If its any use here's the output of sensors and smartctl (though I don't think my motherboard fully supports sensors as its been alarmed for several years now with my old drive and I never had this problem...)

```
w83627thf-isa-0228
Adapter: ISA adapter
VCore:       +1.54 V  (min =  +0.00 V, max =  +3.84 V)   
+12V:       +11.86 V  (min =  +0.43 V, max =  +6.08 V)   ALARM
+3.3V:       +3.49 V  (min =  +1.54 V, max =  +2.72 V)   ALARM
+5V:         +4.96 V  (min =  +0.43 V, max =  +0.11 V)   ALARM
-12V:        +6.06 V  (min =  -4.38 V, max = -13.59 V)   ALARM
V5SB:        +5.08 V  (min =  +0.32 V, max =  +3.09 V)   ALARM
VBat:        +3.26 V  (min =  +0.61 V, max =  +1.02 V)   ALARM
fan1:          0 RPM  (min =  146 RPM, div = 128)  ALARM
CPU Fan:       0 RPM  (min =   -1 RPM, div = 2)  ALARM
fan3:          0 RPM  (min = 15340 RPM, div = 2)  ALARM
M/B Temp:    +33.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPU Temp:    +34.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       -48.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
beep_enable:enabled

```

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HDP725032GLAT80
Serial Number:    GE1040RR0S8Y4A
Firmware Version: GM3OA4CA
User Capacity:    320,072,933,376 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Feb 12 19:09:18 2010 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (5908) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  98) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   054    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   123   123   024    Pre-fail  Always       -       295 (Average 331)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       18
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   020    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       395
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       18
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       20
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       20
194 Temperature_Celsius     0x0002   206   206   000    Old_age   Always       -       29 (Lifetime Min/Max 15/32)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       364         -
# 2  Short offline       Completed without error       00%       183         -

SMART Selective self-test log data structure revision number 1
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

If someone can point me in the right direction on where the fsck logs are kept I can dig them out too, only I tried /var/log/fsck and nothing recent is in there, which I suppose I expect since it wasn't mounted at the time...

---


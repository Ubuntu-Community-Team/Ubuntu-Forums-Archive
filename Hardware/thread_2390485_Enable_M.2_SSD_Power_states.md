---
title: "Enable M.2 SSD Power states"
date: 2018-04-29
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2018-04-29
While i do not care about the energy consumption i do care about the heat
How do i enable power saving on this drive:
```
xubuntu@xubuntu:~$ sudo smartctl /dev/nvme0n1 -x
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-20-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       Force MP500
Serial Number:                      18107956000123380298
Firmware Version:                   E7FM04.C
PCI Vendor/Subsystem ID:            0x1987
IEEE OUI Identifier:                0x6479a7
Controller ID:                      0
Number of Namespaces:               1
Namespace 1 Size/Capacity:          120,034,123,776 [120 GB]
Namespace 1 Formatted LBA Size:     512
Local Time is:                      Sun Apr 29 14:22:33 2018 UTC
Firmware Updates (0x02):            1 Slot
Optional Admin Commands (0x0007):   Security Format Frmw_DL
Optional NVM Commands (0x001e):     Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat
Maximum Data Transfer Size:         512 Pages
[B]Warning  Comp. Temp. Threshold:     110 Celsius
Critical Comp. Temp. Threshold:     130 Celsius[/B]

[B]Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     7.90W       -        -    0  0  0  0        0       0
 1 +     4.00W       -        -    1  1  1  1      600     600
 2 +     3.00W       -        -    2  2  2  2      600     600
 3 -   0.1100W       -        -    3  3  3  3      600     600
 4 -   0.0050W       -        -    4  4  4  4   100000  160000[/B]

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         1
 1 -    4096       0         0

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02, NSID 0x1)
Critical Warning:                   0x00
**Temperature:                        62 Celsius**
Available Spare:                    100%
Available Spare Threshold:          1%
Percentage Used:                    0%
Data Units Read:                    242 [123 MB]
Data Units Written:                 0
Host Read Commands:                 4,263
Host Write Commands:                0
Controller Busy Time:               84
Power Cycles:                       11
Power On Hours:                     1
Unsafe Shutdowns:                   6
Media and Data Integrity Errors:    0
Error Information Log Entries:      1,515
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
**Temperature Sensor 2:               63 Celsius**

Error Information (NVMe Log 0x01, max 64 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0       1515     0  0x0005  0x4004      - 8796109799680     1     -
  1       1514     0  0x0003  0x4004      - 8796109799680     1     -
  2       1513     0  0x0017  0x4004      - 8796109799680     1     -
  3       1512     0  0x0014  0x4004      - 8796109799680     1     -
  4       1511     1  0x0000  0x4016      -            0     1     -
  5       1510     1  0x0000  0x4016      -            0     1     -
  6       1509     1  0x0000  0x4016      -            0     1     -
  7       1508     1  0x0000  0x4016      -            0     1     -
  8       1507     1  0x0000  0x4016      -            0     1     -
  9       1506     1  0x0000  0x4016      -            0     1     -
 10       1505     1  0x0000  0x4016      -            0     1     -
 11       1504     1  0x0000  0x4016      -            0     1     -
 12       1503     1  0x0000  0x4016      -            0     1     -
 13       1502     1  0x0000  0x4016      -            0     1     -
 14       1501     1  0x0000  0x4016      -            0     1     -
 15       1500     1  0x0000  0x4016      -            0     1     -
... (48 entries not shown)
```
Yes the sensor is accurate, the surface temp of the ssd is over 50C
This drive does not even have a parathion on it, so it is idle without a doubt

edit:
```
xubuntu@xubuntu:~$ tree /sys/class/nvme/nvme0
/sys/class/nvme/nvme0
&#9500;&#9472;&#9472; cntlid
&#9500;&#9472;&#9472; dev
&#9500;&#9472;&#9472; device -> ../../../0000:01:00.0
&#9500;&#9472;&#9472; firmware_rev
&#9500;&#9472;&#9472; model
&#9500;&#9472;&#9472; nvme0n1
&#9474;   &#9500;&#9472;&#9472; alignment_offset
&#9474;   &#9500;&#9472;&#9472; bdi -> ../../../../../../virtual/bdi/259:0
&#9474;   &#9500;&#9472;&#9472; capability
&#9474;   &#9500;&#9472;&#9472; dev
&#9474;   &#9500;&#9472;&#9472; device -> ../../nvme0
&#9474;   &#9500;&#9472;&#9472; discard_alignment
&#9474;   &#9500;&#9472;&#9472; ext_range
&#9474;   &#9500;&#9472;&#9472; hidden
&#9474;   &#9500;&#9472;&#9472; holders
&#9474;   &#9500;&#9472;&#9472; inflight
&#9474;   &#9500;&#9472;&#9472; integrity
&#9474;   &#9474;   &#9500;&#9472;&#9472; device_is_integrity_capable
&#9474;   &#9474;   &#9500;&#9472;&#9472; format
&#9474;   &#9474;   &#9500;&#9472;&#9472; protection_interval_bytes
&#9474;   &#9474;   &#9500;&#9472;&#9472; read_verify
&#9474;   &#9474;   &#9500;&#9472;&#9472; tag_size
&#9474;   &#9474;   &#9492;&#9472;&#9472; write_generate
&#9474;   &#9500;&#9472;&#9472; mq
&#9474;   &#9474;   &#9500;&#9472;&#9472; 0
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; cpu0
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; cpu_list
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; nr_reserved_tags
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; nr_tags
&#9474;   &#9474;   &#9500;&#9472;&#9472; 1
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; cpu1
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; cpu_list
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; nr_reserved_tags
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; nr_tags
&#9474;   &#9474;   &#9500;&#9472;&#9472; 2
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; cpu2
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; cpu_list
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; nr_reserved_tags
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; nr_tags
&#9474;   &#9474;   &#9492;&#9472;&#9472; 3
&#9474;   &#9474;       &#9500;&#9472;&#9472; cpu3
&#9474;   &#9474;       &#9500;&#9472;&#9472; cpu_list
&#9474;   &#9474;       &#9500;&#9472;&#9472; nr_reserved_tags
&#9474;   &#9474;       &#9492;&#9472;&#9472; nr_tags
&#9474;   &#9500;&#9472;&#9472; nsid
&#9474;   &#9500;&#9472;&#9472; power
&#9474;   &#9474;   &#9500;&#9472;&#9472; async
&#9474;   &#9474;   &#9500;&#9472;&#9472; autosuspend_delay_ms
&#9474;   &#9474;   &#9500;&#9472;&#9472; control
&#9474;   &#9474;   &#9500;&#9472;&#9472; runtime_active_kids
&#9474;   &#9474;   &#9500;&#9472;&#9472; runtime_active_time
&#9474;   &#9474;   &#9500;&#9472;&#9472; runtime_enabled
&#9474;   &#9474;   &#9500;&#9472;&#9472; runtime_status
&#9474;   &#9474;   &#9500;&#9472;&#9472; runtime_suspended_time
&#9474;   &#9474;   &#9492;&#9472;&#9472; runtime_usage
&#9474;   &#9500;&#9472;&#9472; queue
&#9474;   &#9474;   &#9500;&#9472;&#9472; add_random
&#9474;   &#9474;   &#9500;&#9472;&#9472; chunk_sectors
&#9474;   &#9474;   &#9500;&#9472;&#9472; dax
&#9474;   &#9474;   &#9500;&#9472;&#9472; discard_granularity
&#9474;   &#9474;   &#9500;&#9472;&#9472; discard_max_bytes
&#9474;   &#9474;   &#9500;&#9472;&#9472; discard_max_hw_bytes
&#9474;   &#9474;   &#9500;&#9472;&#9472; discard_zeroes_data
&#9474;   &#9474;   &#9500;&#9472;&#9472; hw_sector_size
&#9474;   &#9474;   &#9500;&#9472;&#9472; io_poll
&#9474;   &#9474;   &#9500;&#9472;&#9472; io_poll_delay
&#9474;   &#9474;   &#9500;&#9472;&#9472; iostats
&#9474;   &#9474;   &#9500;&#9472;&#9472; logical_block_size
&#9474;   &#9474;   &#9500;&#9472;&#9472; max_discard_segments
&#9474;   &#9474;   &#9500;&#9472;&#9472; max_hw_sectors_kb
&#9474;   &#9474;   &#9500;&#9472;&#9472; max_integrity_segments
&#9474;   &#9474;   &#9500;&#9472;&#9472; max_sectors_kb
&#9474;   &#9474;   &#9500;&#9472;&#9472; max_segment_size
&#9474;   &#9474;   &#9500;&#9472;&#9472; max_segments
&#9474;   &#9474;   &#9500;&#9472;&#9472; minimum_io_size
&#9474;   &#9474;   &#9500;&#9472;&#9472; nomerges
&#9474;   &#9474;   &#9500;&#9472;&#9472; nr_requests
&#9474;   &#9474;   &#9500;&#9472;&#9472; optimal_io_size
&#9474;   &#9474;   &#9500;&#9472;&#9472; physical_block_size
&#9474;   &#9474;   &#9500;&#9472;&#9472; read_ahead_kb
&#9474;   &#9474;   &#9500;&#9472;&#9472; rotational
&#9474;   &#9474;   &#9500;&#9472;&#9472; rq_affinity
&#9474;   &#9474;   &#9500;&#9472;&#9472; scheduler
&#9474;   &#9474;   &#9500;&#9472;&#9472; wbt_lat_usec
&#9474;   &#9474;   &#9500;&#9472;&#9472; write_cache
&#9474;   &#9474;   &#9500;&#9472;&#9472; write_same_max_bytes
&#9474;   &#9474;   &#9500;&#9472;&#9472; write_zeroes_max_bytes
&#9474;   &#9474;   &#9492;&#9472;&#9472; zoned
&#9474;   &#9500;&#9472;&#9472; range
&#9474;   &#9500;&#9472;&#9472; removable
&#9474;   &#9500;&#9472;&#9472; ro
&#9474;   &#9500;&#9472;&#9472; size
&#9474;   &#9500;&#9472;&#9472; slaves
&#9474;   &#9500;&#9472;&#9472; stat
&#9474;   &#9500;&#9472;&#9472; subsystem -> ../../../../../../../class/block
&#9474;   &#9500;&#9472;&#9472; trace
&#9474;   &#9474;   &#9500;&#9472;&#9472; act_mask
&#9474;   &#9474;   &#9500;&#9472;&#9472; enable
&#9474;   &#9474;   &#9500;&#9472;&#9472; end_lba
&#9474;   &#9474;   &#9500;&#9472;&#9472; pid
&#9474;   &#9474;   &#9492;&#9472;&#9472; start_lba
&#9474;   &#9500;&#9472;&#9472; uevent
&#9474;   &#9492;&#9472;&#9472; wwid
&#9500;&#9472;&#9472; power
&#9474;   &#9500;&#9472;&#9472; async
&#9474;   &#9500;&#9472;&#9472; autosuspend_delay_ms
&#9474;   &#9500;&#9472;&#9472; control
&#9474;   &#9500;&#9472;&#9472; pm_qos_latency_tolerance_us
&#9474;   &#9500;&#9472;&#9472; runtime_active_kids
&#9474;   &#9500;&#9472;&#9472; runtime_active_time
&#9474;   &#9500;&#9472;&#9472; runtime_enabled
&#9474;   &#9500;&#9472;&#9472; runtime_status
&#9474;   &#9500;&#9472;&#9472; runtime_suspended_time
&#9474;   &#9492;&#9472;&#9472; runtime_usage
&#9500;&#9472;&#9472; rescan_controller
&#9500;&#9472;&#9472; reset_controller
&#9500;&#9472;&#9472; serial
&#9500;&#9472;&#9472; state
&#9500;&#9472;&#9472; subsysnqn
&#9500;&#9472;&#9472; subsystem -> ../../../../../../class/nvme
&#9500;&#9472;&#9472; transport
&#9492;&#9472;&#9472; uevent

22 directories, 100 files
```
```
sudo nvme get-feature -f 0x0c -H /dev/nvme0
get-feature:0xc (Autonomous Power State Transition), Current value:0x000001
    Autonomous Power State Transition Enable (APSTE): Enabled
    Auto PST Entries    .................
    Entry[ 0]   
    .................
    Idle Time Prior to Transition (ITPT): 60 ms
    Idle Transition Power State   (ITPS): 3
    .................
    Entry[ 1]   
    .................
    Idle Time Prior to Transition (ITPT): 60 ms
    Idle Transition Power State   (ITPS): 3
    .................
    Entry[ 2]   
    .................
    Idle Time Prior to Transition (ITPT): 60 ms
    Idle Transition Power State   (ITPS): 3
    .................
    Entry[ 3]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[ 4]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[ 5]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[ 6]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[ 7]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[ 8]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[ 9]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[10]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[11]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[12]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[13]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[14]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[15]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[16]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[17]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[18]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[19]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[20]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[21]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[22]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[23]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[24]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[25]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[26]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[27]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[28]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[29]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[30]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
    Entry[31]   
    .................
    Idle Time Prior to Transition (ITPT): 0 ms
    Idle Transition Power State   (ITPS): 0
    .................
       0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
0000: 18 3c 00 00 00 00 00 00 18 3c 00 00 00 00 00 00 ".<.......<......"
0010: 18 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ".<.............."
0020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
0030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
0040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
0050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
0060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
0070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
0080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
0090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
00a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
00b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
00c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
00d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
00e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"
00f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "................"

```
```
:/~$ for file in /sys/class/nvme/nvme0/subsystem/nvme0/power/* ;do echo -e "$(cat $file)\t$file";done
disabled    /sys/class/nvme/nvme0/subsystem/nvme0/power/async
cat: /sys/class/nvme/nvme0/subsystem/nvme0/power/autosuspend_delay_ms: Input/output error
    /sys/class/nvme/nvme0/subsystem/nvme0/power/autosuspend_delay_ms
auto    /sys/class/nvme/nvme0/subsystem/nvme0/power/control
100000    /sys/class/nvme/nvme0/subsystem/nvme0/power/pm_qos_latency_tolerance_us
0    /sys/class/nvme/nvme0/subsystem/nvme0/power/runtime_active_kids
0    /sys/class/nvme/nvme0/subsystem/nvme0/power/runtime_active_time
disabled    /sys/class/nvme/nvme0/subsystem/nvme0/power/runtime_enabled
unsupported    /sys/class/nvme/nvme0/subsystem/nvme0/power/runtime_status
0    /sys/class/nvme/nvme0/subsystem/nvme0/power/runtime_suspended_time
0    /sys/class/nvme/nvme0/subsystem/nvme0/power/runtime_usage
```

---


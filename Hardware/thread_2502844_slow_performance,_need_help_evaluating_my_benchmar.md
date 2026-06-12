---
title: "slow performance, need help evaluating my benchmarks"
date: 2024-12-02
forum: Hardware
---

### Post by huramentzefix on 2024-12-02
I am running a dual boot system. recently my windows has updated and after that everything was super slow. I suspected chipset drivers at first and updated them.
After that I tried with kaspersky virus scanner and found a trojan.
I then completely wiped my hard drive and installed ubuntu from USB stick and also windows 10 from USB in dual boot.
Now I was running some benchmarks on my ubuntu, can you see anything here which would indicate what the problem is?

```
 [FONT=monospace][COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo smartctl -i /dev/nvme0n1p4 [/COLOR]
smartctl 7.4 2023-08-01 r5530 [x86_64-linux-6.8.0-41-generic] (local build) 
Copyright (C) 2002-23, Bruce Allen, Christian Franke, www.smartmontools.org 

=== START OF INFORMATION SECTION === 
Model Number:                       KBG40ZNV256G KIOXIA 
Serial Number:                      315PC9YZQW82 
Firmware Version:                   HP00AE00 
PCI Vendor/Subsystem ID:            0x1e0f 
IEEE OUI Identifier:                0x8ce38e 
Total NVM Capacity:                 256.060.514.304 [256 GB] 
Unallocated NVM Capacity:           0 
Controller ID:                      0 
NVMe Version:                       1.3 
Number of Namespaces:               1 
Namespace 1 Size/Capacity:          256.060.514.304 [256 GB] 
Namespace 1 Formatted LBA Size:     512 
Namespace 1 IEEE EUI-64:            8ce38e 0401f046a0 
Local Time is:                      Mon Dec  2 09:06:57 2024 AST 

[COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo smartctl -i -a /dev/nvme0n1p4 [/COLOR]
smartctl 7.4 2023-08-01 r5530 [x86_64-linux-6.8.0-41-generic] (local build) 
Copyright (C) 2002-23, Bruce Allen, Christian Franke, www.smartmontools.org 

=== START OF INFORMATION SECTION === 
Model Number:                       KBG40ZNV256G KIOXIA 
Serial Number:                      315PC9YZQW82 
Firmware Version:                   HP00AE00 
PCI Vendor/Subsystem ID:            0x1e0f 
IEEE OUI Identifier:                0x8ce38e 
Total NVM Capacity:                 256.060.514.304 [256 GB] 
Unallocated NVM Capacity:           0 
Controller ID:                      0 
NVMe Version:                       1.3 
Number of Namespaces:               1 
Namespace 1 Size/Capacity:          256.060.514.304 [256 GB] 
Namespace 1 Formatted LBA Size:     512 
Namespace 1 IEEE EUI-64:            8ce38e 0401f046a0 
Local Time is:                      Mon Dec  2 09:07:30 2024 AST 
Firmware Updates (0x14):            2 Slots, no Reset required 
Optional Admin Commands (0x001f):   Security Format Frmw_DL NS_Mngmt Self_Test 
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp 
Log Page Attributes (0x0e):         Cmd_Eff_Lg Ext_Get_Lg Telmtry_Lg 
Maximum Data Transfer Size:         512 Pages 
Warning  Comp. Temp. Threshold:     79 Celsius 
Critical Comp. Temp. Threshold:     84 Celsius 

Supported Power States 
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat 
0 +     3.60W       -        -    0  0  0  0        1       1 
1 +     2.60W       -        -    1  1  1  1        1       1 
2 +     1.80W       -        -    2  2  2  2        1       1 
3 -   0.0500W       -        -    4  4  4  4      800    1200 
4 -   0.0050W       -        -    4  4  4  4     3000   32000 

Supported LBA Sizes (NSID 0x1) 
Id Fmt  Data  Metadt  Rel_Perf 
0 +     512       0         3 
1 -    4096       0         1 

=== START OF SMART DATA SECTION === 
SMART overall-health self-assessment test result: PASSED 

SMART/Health Information (NVMe Log 0x02) 
Critical Warning:                   0x00 
Temperature:                        29 Celsius 
Available Spare:                    100% 
Available Spare Threshold:          5% 
Percentage Used:                    43% 
Data Units Read:                    222.125.428 [113 TB] 
Data Units Written:                 89.878.440 [46,0 TB] 
Host Read Commands:                 3.827.336.290 
Host Write Commands:                753.817.502 
Controller Busy Time:               10.026 
Power Cycles:                       79.658 
Power On Hours:                     11.923 
Unsafe Shutdowns:                   63 
Media and Data Integrity Errors:    0 
Error Information Log Entries:      54 
Warning  Comp. Temperature Time:    0 
Critical Comp. Temperature Time:    0 
Temperature Sensor 1:               29 Celsius 

Error Information (NVMe Log 0x01, 16 of 256 entries) 
No Errors Logged 

Self-test Log (NVMe Log 0x06) 
Self-test status: No self-test in progress 
No Self-tests Logged 

[COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo hdparm -Ttv /dev/nvme0n1p4 [/COLOR]
[sudo] password for ubnt:  

/dev/nvme0n1p4: 
readonly      =  0 (off) 
readahead     = 256 (on) 
geometry      = 61440/64/32, sectors = 125829120, start = 374288384 
Timing cached reads:   1974 MB in  1.99 seconds = 990.10 MB/sec 
Timing buffered disk reads: 412 MB in  3.01 seconds = 136.67 MB/sec 
[COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo hdparm -Ttv /dev/nvme0n1p4 [/COLOR]

/dev/nvme0n1p4: 
readonly      =  0 (off) 
readahead     = 256 (on) 
geometry      = 61440/64/32, sectors = 125829120, start = 374288384 
Timing cached reads:   1966 MB in  1.99 seconds = 987.12 MB/sec 
Timing buffered disk reads: 408 MB in  3.00 seconds = 135.90 MB/sec 
[COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo hdparm  -Tt --direct /dev/nvme0n1p4 [/COLOR]

/dev/nvme0n1p4: 
Timing O_DIRECT cached reads:   876 MB in  2.00 seconds = 438.77 MB/sec 
Timing O_DIRECT disk reads: 1470 MB in  3.00 seconds = 489.61 MB/sec 
[COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo hdparm  -Tt /dev/nvme0n1p4 [/COLOR]

/dev/nvme0n1p4: 
Timing cached reads:   1972 MB in  1.99 seconds = 989.31 MB/sec 
Timing buffered disk reads: 458 MB in  3.01 seconds = 152.32 MB/sec 
[COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sysbench memory --memory-block-size=1G --memory-total-size=20G --memory-oper=write run [/COLOR]
sysbench 1.0.20 (using system LuaJIT 2.1.0-beta3) 

Running the test with following options: 
Number of threads: 1 
Initializing random number generator from current time 


Running memory speed test with the following options: 
 block size: 1048576KiB 
 total size: 20480MiB 
 operation: write 
 scope: global 

Initializing worker threads... 

Threads started! 

Total operations: 9 (    0.81 per second) 

9216.00 MiB transferred (828.81 MiB/sec) 


General statistics: 
   total time:                          11.1073s 
   total number of events:              9 

Latency (ms): 
        min:                                 1229.64 
        avg:                                 1234.03 
        max:                                 1245.74 
        95th percentile:                     1235.62 
        sum:                                11106.26 

Threads fairness: 
   events (avg/stddev):           9.0000/0.00 
   execution time (avg/stddev):   11.1063/0.00 

[COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sysbench memory --memory-block-size=1G --memory-total-size=20G --memory-oper=read run [/COLOR]
sysbench 1.0.20 (using system LuaJIT 2.1.0-beta3) 

Running the test with following options: 
Number of threads: 1 
Initializing random number generator from current time 


Running memory speed test with the following options: 
 block size: 1048576KiB 
 total size: 20480MiB 
 operation: read 
 scope: global 

Initializing worker threads... 

Threads started! 

Total operations: 19 (    1.88 per second) 

19456.00 MiB transferred (1926.07 MiB/sec) 


General statistics: 
   total time:                          10.0889s 
   total number of events:              19 

Latency (ms): 
        min:                                  529.83 
        avg:                                  530.90 
        max:                                  533.13 
        95th percentile:                      530.08 
        sum:                                10087.16 

Threads fairness: 
   events (avg/stddev):           19.0000/0.00 
   execution time (avg/stddev):   10.0872/0.00 

[COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo dmidecode -t 17 | grep -i "speed" [/COLOR]
       [COLOR=#ff5454]**Speed**[/COLOR][COLOR=#000000]: 3200 MT/s [/COLOR]
       Configured Memory [COLOR=#ff5454]**Speed**[/COLOR][COLOR=#000000]: 2667 MT/s [/COLOR]
       [COLOR=#ff5454]**Speed**[/COLOR][COLOR=#000000]: 3200 MT/s [/COLOR]
       Configured Memory [COLOR=#ff5454]**Speed**[/COLOR][COLOR=#000000]: 2667 MT/s [/COLOR]
[COLOR=#54ff54]**ubnt@laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sysbench memory --memory-block-size=1G --memory-total-size=16G --memory-oper=write --threads=1 run [/COLOR]
sysbench 1.0.20 (using system LuaJIT 2.1.0-beta3) 

Running the test with following options: 
Number of threads: 1 
Initializing random number generator from current time 


Running memory speed test with the following options: 
 block size: 1048576KiB 
 total size: 16384MiB 
 operation: write 
 scope: global 

Initializing worker threads... 

Threads started! 

Total operations: 9 (    0.81 per second) 

9216.00 MiB transferred (829.89 MiB/sec) 


General statistics: 
   total time:                          11.0929s 
   total number of events:              9 

Latency (ms): 
        min:                                 1231.46 
        avg:                                 1232.41 
        max:                                 1234.31 
        95th percentile:                     1235.62 
        sum:                                11091.70 

Threads fairness: 
   events (avg/stddev):           9.0000/0.00 
   execution time (avg/stddev):   11.0917/0.00[/FONT]
  
```

thanks!

---

### Post by TheFu on 2024-12-02
First, a basic overview of the system would be helpful.  **inxi -bz** would provide that. -b is brief. -z removes S/N information and other things that could be tracked.  Always helpful to post that with any HW issue, so people have a place to start.

Use the **nvme** tool, that's the name, rather than **smartctl**, for NVMe storage information and health.

There have been UEFI viruses found that can infect an OS. My understanding is that they are OS specific and write the virus boot code into the firmware of the motherboard. Of course, MS-Windows is the main target, but there have been Linux-specific variants as well.  Both are blocked by using UEFI + SecureBoot.  You might check that is you are booting with UEFI, that SecureBoot is also enabled.  Being in a dualboot setup with a supported version of MS-Windows restricts your easy ability to use Legacy/BIOS booting in Linux, but it is possible with some hassle (have to toggle the BIOS boot type every time).

When you say "things are slow", that's extremely broad. Hard for anyone to get specific enough to really help.  If you could use some specific programs that are commonly used, perhaps someone who also uses those tools would be able to speak to issues?

As a comparison, 
```
$ sudo hdparm -Ttv /dev/nvme0n1p4

/dev/nvme0n1p4:
 HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 512 (on)
 HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device
 geometry      = 953117/64/32, sectors = 1951985039, start = 1540096
 Timing cached reads:   41144 MB in  1.99 seconds = 20676.33 MB/sec
 HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device
 Timing buffered disk reads: 5072 MB in  3.00 seconds = 1690.32 MB/sec
```
and
```
$ sudo hdparm  -Tt --direct /dev/nvme0n1p4

/dev/nvme0n1p4:
 Timing O_DIRECT cached reads:   4546 MB in  2.00 seconds = 2274.29 MB/sec
 HDIO_DRIVE_CMD(identify) failed: Inappropriate ioctl for device
 Timing O_DIRECT disk reads: 5370 MB in  3.00 seconds = 1789.69 MB/sec
```

So, it seems that the performance of your SSD is massively slower than mine.  No NVMe SSD should be that slow (yours, not mine).  Here's the SMART information for my NVMe drive:
```
$ sudo nvme smart-log  /dev/nvme0n1
Smart Log for NVME device:nvme0n1 namespace-id:ffffffff
critical_warning                    : 0
temperature                         : 37 C
available_spare                     : 100%
available_spare_threshold           : 10%
percentage_used                     : 2%
data_units_read                     : 15,149,741
data_units_written                  : 32,251,324
host_read_commands                  : 144,685,574
host_write_commands                 : 590,073,169
controller_busy_time                : 536
power_cycles                        : 27
power_on_hours                      : 1,508
unsafe_shutdowns                    : 13
media_errors                        : 0
num_err_log_entries                 : 0
Warning Temperature Time            : 0
Critical Composite Temperature Time : 0
Temperature Sensor 1                : 37 C
Temperature Sensor 2                : 46 C
Thermal Management T1 Trans Count   : 0
Thermal Management T2 Trans Count   : 0
Thermal Management T1 Total Time    : 0
Thermal Management T2 Total Time    : 0

```
It is a Samsung 980 using an m.2 slot on the B450 motherboard.  Less than 50% of the storage is allocated for use, so there are plenty of cells available for load balancing.  As SSD cells get older (more writes to the same cells), they get slower.  I've had 2 SSDs go bad, but they were 1st generation SSDs, so nothing like what we all have today.  They got slower and slower and slower, would turn "read-only"  and cause OS crashes.  Also, this system is running Ubuntu Server 20.04, not 22.04.

I have a KIOXIA SSD in a Dell laptop (product: KXG60ZNV512G NVMe KIOXIA 512GB). It's not powered on now, so I can't easily get the data from that device.  Screw it ... I'll go turn it on.  I remember being a little disappointed in the SSD when the laptop arrived.  Of course, I wiped it and put a Linux on it immediately. I don't dual boot.  Ok, it is booted and unlocked.  For laptops, I always use LUKS encryption. Also, it has LM 22 on it, not Ubuntu 22.04.
```
$ sudo hdparm -Ttv /dev/nvme0n1p3

/dev/nvme0n1p3:
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 486164/64/32, sectors = 995663872, start = 4550656
 Timing cached reads:   36182 MB in  2.00 seconds = 18126.49 MB/sec
 Timing buffered disk reads: 4438 MB in  3.00 seconds = 1479.29 MB/sec
```

and

```
$ sudo hdparm -Tt  --direct  /dev/nvme0n1p3

/dev/nvme0n1p3:
 Timing O_DIRECT cached reads:   4018 MB in  2.00 seconds = 2008.54 MB/sec
 Timing O_DIRECT disk reads: 6878 MB in  3.00 seconds = 2292.27 MB/sec
```

and FWIW, 

```
$ sudo nvme smart-log /dev/nvme0n1
Smart Log for NVME device:nvme0n1 namespace-id:ffffffff
critical_warning                        : 0
temperature                             : 25 °C (298 K)
available_spare                         : 100%
available_spare_threshold               : 10%
percentage_used                         : 13%
endurance group critical warning summary: 0
Data Units Read                         : 41069646 (21.03 TB)
Data Units Written                      : 58587882 (30.00 TB)
host_read_commands                      : 890019342
host_write_commands                     : 2323965034
controller_busy_time                    : 2779
power_cycles                            : 828
power_on_hours                          : 9714
unsafe_shutdowns                        : 23
media_errors                            : 0
num_err_log_entries                     : 3
Warning Temperature Time                : 0
Critical Composite Temperature Time     : 0
Temperature Sensor 1           : 25 °C (298 K)
Thermal Management T1 Trans Count       : 0
Thermal Management T2 Trans Count       : 0
Thermal Management T1 Total Time        : 0
Thermal Management T2 Total Time        : 0

```

And FWIW, the laptop HW overview:
```
$ inxi -bz
System:
  Kernel: **6.8.0-48-generic** arch: x86_64 bits: 64
  Console: pty pts/3 Distro: **Linux Mint 22** Wilma
Machine:
  Type: Laptop System: Dell product: Latitude 5320 v: N/A serial: <superuser required>
  Mobo: Dell model: 0Y7GXY v: A00 serial: <superuser required> UEFI: Dell v: 1.36.0
    date: 03/22/2024
Battery:
  ID-1: BAT0 charge: 49.5 Wh (100.0%) condition: 49.5/61.8 Wh (80.1%) volts: 15.6 min: 15.2
CPU:
  Info: quad core 11th Gen Intel **Core i5-1145G7** [MT MCP] speed (MHz): avg: 579 min/max: 400/4400
Graphics:
  Device-1: Intel TigerLake-LP GT2 [**Iris Xe Graphics**] driver: i915 v: kernel
  Device-2: Realtek Integrated_Webcam_HD driver: uvcvideo type: USB
  **Display: x11 server: X.org** v: 1.21.1.11 with: Xwayland v: 23.2.6 driver: X:
    loaded: modesetting unloaded: fbdev,vesa dri: iris gpu: i915 tty: 115x31 resolution: 1920x1080
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: mesa v: 24.0.9-0ubuntu0.2 note: console (EGL sourced)
    renderer: Mesa Intel Xe Graphics (TGL GT2), llvmpipe (LLVM 17.0.6 256 bits)
Network:
  Device-1: Intel Wi-Fi 6 AX201 driver: iwlwifi
  Device-2: **ASIX AX88179 Gigabit Ethernet** driver: ax88179_178a type: USB
Drives:
  Local Storage: total: 476.94 GiB used: 10.43 GiB (2.2%)
Info:
  **Memory: total: 16 GiB** note: est. available: 15.35 GiB used: 3.26 GiB (21.2%)
  Processes: 324 **Uptime: 15d 23h 38m** Init: systemd target: graphical (5) Shell: Bash
    inxi: 3.3.34
```
If is a very stable system.  The uptime is really mostly standby time.  It goes into and out of standby without any issues. I don't do Wayland and avoid using wifi. Plenty of CPU and RAM for a laptop.  Only 1 internal SSD, barely used.  I don't keep anything important on laptops.

If I wanted to see real storage performance, I'd use **fio**.  I know there are GUI performance testing tools in KDE and I think Gnome-Disks has something, but neither of those tools are on my systems.  Here's an article about running fio tests with large reads, large writes, random reads and random writes and mixed workloads. [https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/](https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/) explains how to use fio.

Most of my "servers" run 5-10 virtual machines, so the storage is mostly random reads+writes 24/7.  Also, the servers have NFS storage, so consistent streaming to other devices of larger files happens. All devices are wired GigE connected and there's a caching DNS on my LAN to prevent slow responses.  Slow DNS can make a system feel slow.

RAM and CPU are things we can't do anything about, unless we tweak the kernel to disable known CPU protections against attacks. I've never done that. The default protections are enabled.  I do see that you have mixed speed in your RAM.  I had issues with RAM in my first Ryzen 2600 after adding 16GB (2x8GB) more to the system. In theory, it was all the same part number from the same manufacturer and all certified for 3200Mhz, but in practice, that caused an unstable system when all 4 slots were filled.  If I used either of the two pairs at 3200Mhz, it worked fine, but with both pairs in the system, I had to slow down to 2666 Mhz for stability reasons.  I fixed that later, by getting 32GB of RAM in 2x16GB sticks.  Automatic OC using the built-in MB OC tool provides 7% more performance - or so it claims.  I didn't try to manually achieve higher OC.  The systems the Ryzen was replacing were all significantly slower - Pentium or 1st-gen Core i5 systems, so 8-10x slower.  I didn't bother with bench marking before/after the RAM changes.  I sold the used RAM to friends for cheap.  With Ryzen, I found that only "matched" RAM worked for me.  I spent far too much time tweaking speeds to get the fastest I could while still being stable.  I understand that Intel CPUs/MBs aren't picky at all.

I would concentrate efforts on the SSD performance. That is clearly an issue.

Anyway, some ideas for your consideration.  These forums are about to go read-only. Beware of that.

---


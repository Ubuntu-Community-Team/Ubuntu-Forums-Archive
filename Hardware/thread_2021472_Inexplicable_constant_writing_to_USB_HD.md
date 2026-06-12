---
title: "Inexplicable constant writing to USB HD"
date: 2012-07-09
forum: Hardware
---

### Post by Ranko Kohime on 2012-07-09
I've recently formatted a 1TB desktop drive to use for a variety of purposes, with Windows 7 on one 80GB partition, (as well as the ~100MB Recovery partition), and the rest is a blank EXT4 partition.

Whenever the EXT4 partition is mounted, conky reports a constant 4MB/s write to the drive (/dev/sdc).  iotop reports 4MB/s write at the top, under total disk write, but it doesn't show a process making those writes, even if I select the write column.

The writing stops when I unmount that particular partition, and starts right back up within 2-3 seconds after I mount it.

The hard drive light is blinking rhythmically, as if the writes are actually occurring.  The drive is connected through a USB-Sata dock.

So, I don't know...  Linux poltergeist, perhaps?  :confused:

---

### Post by Redblade20XX on 2012-07-09
Can you post the output of,

```
top
```

when you observe the hdd light acting up?

- Red

---

### Post by Ranko Kohime on 2012-07-14
```
top - 07:19:25 up 1 day, 22:13,  2 users,  load average: 1.02, 0.77, 0.62
Tasks: 245 total,   1 running, 243 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.4%us,  1.3%sy,  0.0%ni, 97.2%id,  0.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8087508k total,  3652780k used,  4434728k free,   112096k buffers
Swap:   524284k total,        0k used,   524284k free,   780300k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                   
 1745 root      20   0  210m  52m  14m S    5  0.7  98:04.08 Xorg                                                                      
 2495 ranko     20   0  674m 3900 2300 S    2  0.0  44:10.79 conky                                                                     
 4824 ranko     20   0  558m  16m 9.8m S    2  0.2   0:14.24 sakura                                                                    
 2352 ranko     20   0 1628m 107m  27m S    2  1.4 100:34.72 compiz                                                                    
 2789 ranko     20   0  657m  38m  11m S    1  0.5  21:51.42 unity-panel-ser                                                           
 2196 ranko     20   0 52044  26m  628 S    0  0.3   8:21.89 dbus-daemon                                                               
 2401 ranko     20   0 20168  944  772 S    0  0.0   1:11.80 syndaemon                                                                 
 2477 ranko     20   0  846m  24m  13m S    0  0.3   0:08.55 nautilus                                                                  
 2819 ranko     20   0  410m 9.8m 7444 S    0  0.1   0:00.29 indicator-print                                                           
 2929 ranko     20   0  416m  10m 7688 S    0  0.1   0:00.22 telepathy-indic                                                           
 3549 ranko     20   0  876m 221m  38m S    0  2.8  17:09.69 chromium-browse                                                           
 3668 ranko     20   0  916m 106m  19m S    0  1.3   1:54.86 chromium-browse                                                           
 3724 ranko     20   0  872m  59m  17m S    0  0.8   9:06.46 chromium-browse                                                           
 3801 ranko     20   0 4297m  74m  12m S    0  0.9   2:38.29 java                                                                      
25857 root      20   0     0    0    0 S    0  0.0   0:00.43 kworker/0:0                                                               
26130 ranko     20   0 17464 1432  964 R    0  0.0   0:00.34 top                                                                       
    1 root      20   0 24556 2388 1280 S    0  0.0   0:01.37 init                                                                      
    2 root      20   0     0    0    0 S    0  0.0   0:00.06 kthreadd                                                                  
    3 root      20   0     0    0    0 S    0  0.0  13:29.10 ksoftirqd/0                                                               
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                               
    7 root      RT   0     0    0    0 S    0  0.0   0:00.92 watchdog/0                                                                
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                               
   10 root      20   0     0    0    0 S    0  0.0   1:09.01 ksoftirqd/1                                                               
   12 root      RT   0     0    0    0 S    0  0.0   0:01.16 watchdog/1                                                                
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                               
   15 root      20   0     0    0    0 S    0  0.0  24:00.73 ksoftirqd/2                                                               
   16 root      RT   0     0    0    0 S    0  0.0   0:00.77 watchdog/2                                                                
   17 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                                                               
   19 root      20   0     0    0    0 S    0  0.0   1:28.17 ksoftirqd/3                                                               
   20 root      RT   0     0    0    0 S    0  0.0   0:01.08 watchdog/3                                                                
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                    
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                   
```
```
Total DISK READ:       0.00 B/s | Total DISK WRITE:    1940.37 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                                                 
26035 be/3 root          0.00 B      4.00 K  0.00 %  0.06 % [jbd2/sdc3-8]
  337 be/3 root          0.00 B      4.00 K  0.00 %  0.01 % [jbd2/dm-0-8]
    1 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % init
    2 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [kthreadd]
    3 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [ksoftirqd/0]
    6 rt/4 root          0.00 B      0.00 B  0.00 %  0.00 % [migration/0]
    7 rt/4 root          0.00 B      0.00 B  0.00 %  0.00 % [watchdog/0]
    8 rt/4 root          0.00 B      0.00 B  0.00 %  0.00 % [migration/1]
 2057 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [flush-252:0]
   10 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [ksoftirqd/1]
   12 rt/4 root          0.00 B      0.00 B  0.00 %  0.00 % [watchdog/1]
   13 rt/4 root          0.00 B      0.00 B  0.00 %  0.00 % [migration/2]
 2062 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % console-kit-daemon --no-daemon
   15 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [ksoftirqd/2]
   16 rt/4 root          0.00 B      0.00 B  0.00 %  0.00 % [watchdog/2]
   17 rt/4 root          0.00 B      0.00 B  0.00 %  0.00 % [migration/3]
 2066 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % console-kit-daemon --no-daemon
   19 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [ksoftirqd/3]
   20 rt/4 root          0.00 B      0.00 B  0.00 %  0.00 % [watchdog/3]
   21 be/0 root          0.00 B      0.00 B  0.00 %  0.00 % [cpuset]
   22 be/0 root          0.00 B      0.00 B  0.00 %  0.00 % [khelper]
   23 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [kdevtmpfs]
   24 be/0 root          0.00 B      0.00 B  0.00 %  0.00 % [netns]
 2073 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % console-kit-daemon --no-daemon
   26 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [sync_supers]
   27 be/4 root          0.00 B      0.00 B  0.00 %  0.00 % [bdi-default]
   28 be/0 root          0.00 B      0.00 B  0.00 %  0.00 % [kintegrityd]

```

Same thing, different physical disk, with same partition layout as the first one.  Windows 7 with it's System Reserved as the first two partitions, 3rd is EXT4, and it gets written to when mounted, even though it's empty.

The output of iotop is sorted by the write column.  It's showing the write happening to disk under total, but not a process to attach to it!?

The problem seems to go away as soon as I start filling the partition with files.

---


---
title: "System stuttering under heavy SSD load"
date: 2014-03-27
forum: Hardware
---

### Post by Freek07 on 2014-03-27
When there's a heavy workload on SSD (e.g. vi save huge file, split huge file, etc), the audio (and the system) starts stuttering. Same happens when I start vmware machine (heavy load while windows is booting).
The mouse get "jumpy",... 

Virtual machine AND music are on second ssd (so SSD util is not the reason!).
Here is example from iostat:

[FONT=Courier New]avg-cpu:  %user   %nice %system %iowait  %steal   %idle                                                                                                      
           6.55    0.00    2.33   16.59    0.00   74.52                                                                                                      
                                                                                                                                                             
Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util                                    
sda               3.20     2.40  722.40  168.00    89.58    80.34   390.84    34.87   39.17    0.80  204.14   0.58  51.52                                    
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00    0.00    0.00   0.00   0.00                                    
sdc               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00    0.00    0.00   0.00   0.00                                    
sdd               0.00     0.00    2.00    0.00     0.08     0.00    79.20     0.00    1.20    1.20    0.00   0.80   0.16     [/FONT]                              

where sda is primary disk. Here it's only 50% "util" but it was much more stuttering than on 100% util like here:
[FONT=Courier New]avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          20.04    0.00    4.30    4.10    0.00   71.57

Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               0.40    11.20 1650.80    0.40   410.70     0.05   509.45     1.35    0.82    0.82    2.00   0.60  99.84
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00    0.00    0.00   0.00   0.00
sdc               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00    0.00    0.00   0.00   0.00
sdd               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00    0.00    0.00   0.00   0.00[/FONT]

Drives are crucial M4.
This is my controller:
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)

This is dmesg containit SATA:
$ dmesg | grep SATA
[    0.842552] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x13 impl SATA mode
[    0.859726] ata1: SATA max UDMA/133 abar m2048@0xf5338000 port 0xf5338100 irq 42
[    0.859729] ata2: SATA max UDMA/133 abar m2048@0xf5338000 port 0xf5338180 irq 42
[    0.859733] ata5: SATA max UDMA/133 abar m2048@0xf5338000 port 0xf5338300 irq 42
[    1.178477] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.498310] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.818189] ata5: SATA link down (SStatus 0 SControl 300)

Any ideas on how to prevent stuttering?

---

### Post by Freek07 on 2014-04-16
Answering myself: switched scheduler from CFQ to DEADLINE and it works without stutterin...

---


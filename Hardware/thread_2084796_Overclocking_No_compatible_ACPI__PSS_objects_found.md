---
title: "Overclocking: No compatible ACPI _PSS objects found."
date: 2012-11-16
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2012-11-16
Xubuntu 12.10 64bit; [My hardware]("http://www.eggxpert.com/forums/ShowPost.aspx?PostID=831287#831287")
I was [doing a little overclocking]("http://www.overclockers.com/forums/showthread.php?t=720818") and I hit a error at 3.8GHz (end of page 2), so I backed off to 3.7GHz, for the record I have the latest BIOS
&#8595; @ 3.8GHz
```
~$ dmesg | grep -i firmware 
[    1.385124] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found. 
[    1.385124] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
```&#8595; @ 3.7GHz
```
~$ dmesg | grep MHz
[    0.004000] tsc: Detected 3700.361 MHz processor
[    0.334857] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    1.387985] powernow-k8:    0 : pstate 0 (3700 MHz)
[    1.387986] powernow-k8:    1 : pstate 1 (2700 MHz)
[    1.387986] powernow-k8:    2 : pstate 2 (2200 MHz)
[    1.387987] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.988425] tsc: Refined TSC clocksource calibration: 3700.000 MHz
~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies 
3700000 2700000 2200000 800000 
3700000 2700000 2200000 800000 
3700000 2700000 2200000 800000 
3700000 2700000 2200000 800000
```If I go to 3.8GHz it acts like my Cool n Quiet feature is disabled, as a result I get no stepping 
Is there a 1GHz barrier between steps or something?
here is a larger dmesg
&#8595; @ 3.8GHz
```
[    1.380088] cpuidle: using governor ladder
[    1.380089] cpuidle: using governor menu
[    1.380090] EFI Variables Facility v0.08 2004-May-17
[    1.380237] ashmem: initialized
[    1.380314] TCP: cubic registered
[    1.380370] NET: Registered protocol family 10
[    1.380470] NET: Registered protocol family 17
[    1.380478] Key type dns_resolver registered
[    1.380652] PM: Hibernation image not present or could not be loaded.
[    1.380658] registered taskstats version 1
[    1.382592] Key type trusted registered
[    1.383711] Key type encrypted registered
[    1.385025]   Magic number: 4:339:342
[    1.385114] rtc_cmos 00:02: setting system clock to 2012-11-15 18:20:48 UTC (1353003648)
[    1.385147] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor (4 cpu cores) (version 2.20.00)
[B][    1.385153] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.385153] [Firmware Bug]: powernow-k8: Try again with latest BIOS.[/B]
[    1.385234] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.385234] EDD information not available.
[    1.403008] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.547017] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.547050] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.548674] ata4.00: ATA-8: WDC WD800AAJS-55M0A0, 01.03E01, max UDMA/133
[    1.548677] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.549473] ata4.00: configured for UDMA/133
[    1.549507] ata2.00: ATAPI: ATAPI   iHAS124   B, AL0L, max UDMA/100
[    1.550335] ata2.00: configured for UDMA/100
[    1.552291] scsi 1:0:0:0: CD-ROM            ATAPI    iHAS124   B      AL0L PQ: 0 ANSI: 5
[    1.555641] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.555643] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.555719] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.555775] sr 1:0:0:0: Attached scsi generic sg0 type 5
```

---


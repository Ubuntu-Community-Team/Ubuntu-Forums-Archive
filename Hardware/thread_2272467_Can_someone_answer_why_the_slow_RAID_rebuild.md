---
title: "Can someone answer why the slow RAID rebuild?"
date: 2015-04-07
forum: Hardware
---

### Post by litch84 on 2015-04-07
/dev/sde failed so I threw another (different model) in there and started the rebuild.

It crashed within minutes, hddtemp yielded the new disk was hitting 51*C! So I limited the rebuild speed to 10MB/s and stuck a bench fan on the case - new temps are far more appealing.

```

/dev/sda: ST3000DM001-1CH166: 24°C
/dev/sdb: ST3000DM001-1CH166: 25°C
/dev/sdc: ST3000DM001-1CH166: 25°C
/dev/sdd: ST3000DM001-1CH166: 25°C
/dev/sde: ST33000651AS: 28°C

```

Fast forward 30 hours - and previously rebuilding at 10MB/s (limited by raid/speed_limit_max sysctl to reduce heat generation) it got to 87% rebuilt, but now only rebuilds at ~1MB/s even when max limit is increase to 20K...

SATA protocol error seems to coincide with the slow down:

```

[170775.261439] ata9.00: exception Emask 0x0 SAct 0x600000 SErr 0x0 action 0x6 frozen
[170775.262102] ata9.00: failed command: WRITE FPDMA QUEUED
[170775.262749] ata9.00: cmd 61/00:a8:40:19:cc/04:00:1d:01:00/40 tag 21 ncq 524288 out
[170775.262749]          res 40/00:00:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[170775.264070] ata9.00: status: { DRDY }
[170775.264731] ata9.00: failed command: WRITE FPDMA QUEUED
[170775.265394] ata9.00: cmd 61/00:b0:40:1d:cc/04:00:1d:01:00/40 tag 22 ncq 524288 out
[170775.265394]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[170775.266743] ata9.00: status: { DRDY }
[170775.267415] ata9: hard resetting link
[170777.361084] ata9: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[170778.299007] ata9.00: configured for UDMA/133
[170778.299017] ata9.00: device reported invalid CHS sector 0
[170778.299021] ata9.00: device reported invalid CHS sector 0
[170778.299031] ata9: EH complete

```

And IO stats seem to indicate the new drive is _not_ performing well at all (writing at 8MB/s but await = 70ms and util% is near 70%)

```
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.18    0.00    0.72    0.01    0.00   99.10


Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda            2047.90     0.00   16.36    0.17  8256.99     0.08   999.52     0.04    2.14    1.70   46.09   1.84   3.04
sdb            2047.89     0.00   16.36    0.17  8256.98     0.08   999.57     0.04    2.16    1.71   46.17   1.85   3.05
sdc            2047.90     0.00   16.36    0.17  8256.98     0.08   999.55     0.05    3.10    2.65   46.92   2.76   4.56
sdd            2047.89     0.00   16.36    0.17  8256.98     0.08   999.58     0.05    3.08    2.63   47.03   2.75   4.55
sde               0.01  2047.89    0.00   16.52     0.00  8257.05   999.64     1.14   69.25   22.34   69.25  41.50  68.56
sdf               0.29     0.00    0.08    0.17     1.70     0.67    19.49     0.00    0.82    1.10    0.69   0.60   0.01
md0               0.00     0.00    0.00    0.00     0.01     0.00     3.82     0.00    0.00    0.00    0.00   0.00   0.00

```

raid/speed_limit_min = 1K (1MB/s)
raid/speed_limit_max = 20K (20MB/s)

The questions:
Will the RAID rebuild resume from where it is now if I reboot (which should kick the new drive back into full speed) or will it start from 0% again?
Is there a way to pause the rebuild at current progress so I can manually yank the power out the HDD and power reset it that way?

Thanks in advance...

---

### Post by tgalati4 on 2015-04-07
Hard to say.  It's possible that you are having a problem with a cable or the SATA controller on the motherboard.  Try moving cables around and cleaning up the motherboard.

51C is not unusual for a 7200 RPM drive that is performing constant writes.  The other drives are only reading (which uses 1/2 the power), so they will be cooler.  What are the SMART parameters of /dev/sde?  Perhaps there is an issue with the drive, cable, or SATA controller that caused the original to fail and is now causing the replacement to have issues.

What are the SMART parameters of the drive that failed?  If they are similar, then you know something else is going on.

---


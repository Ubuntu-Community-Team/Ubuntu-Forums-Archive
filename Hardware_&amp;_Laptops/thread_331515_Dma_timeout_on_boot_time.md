---
title: "Dma timeout on boot time"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by pablovp on 2007-01-04
I'm using Kubuntu Edgy kernel 2.6.17-10-generic, running on a Acer Travelmate 4402WLMi laptop.

Dma hangs during boot time, the messages are exactly the same that on this thread : [http://ubuntuforums.org/showthread.php?t=9914&highlight=dma+timeout](http://ubuntuforums.org/showthread.php?t=9914&highlight=dma+timeout)

hda: timeout waiting for DMA
hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }

Kernel hangs, and doesn't boot anymore.

I've tried a couple of things that didn't  worked: 
* Disabled dma on hda at hdparm
* Enabled dma on hda, but with acoustic management turned off: hdparm -B255 -a32 -X69 -u1 -m16 -c3 /dev/hda
* On dapper there was no such problem.

I turned off dma on boot with the option ide=nodma on grub, with this option i can boot, but performance dropped a lot, buffered disk read time dropped from 36 MB/sec to 3 MB/s, and the time to boot is 20 seconds slower.

So, disabling DMA is not an option for me.

I Tested the hard disk(Hitachi Travelstar 5K100) with smartctl and DMA is enabled on windows, so that is not a hardware problem.

Should i try a kernel upgrade? anyone solved that problem without disabling DMA?

---

### Post by pablovp on 2007-01-04
Got it fixed.

I removed the hda line from /etc/hdparm.conf and added it to /etc/init.d/bootmisc.sh.

I think it was a timing issue, maybe the driver was not ready at that time.

---

### Post by cygnus81 on 2007-04-23
I have roughly the same problem, only it doesn't freeze - it just hangs for a few moments (probably the timeout period) and then moves on. Furthermore, I can access the disk when the system is loaded.

Here is the relevant portion of the syslog:
```

Apr 23 09:58:52 localhost kernel: [17179574.180000] Probing IDE interface ide1...
Apr 23 09:58:52 localhost kernel: [17179575.044000] hdc: SONY CD-ROM CDU523 1, ATAPI CD/DVD-ROM drive
Apr 23 09:58:52 localhost kernel: [17179575.324000] **hdd: MAXTOR 6L020J1, ATA DISK drive**
Apr 23 09:58:52 localhost kernel: [17179575.380000] ide1 at 0x170-0x177,0x376 on irq 15
Apr 23 09:58:52 localhost kernel: [17179575.388000] hda: max request size: 1024KiB
Apr 23 09:58:52 localhost kernel: [17179575.404000] hda: 78156288 sectors (40016 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
Apr 23 09:58:52 localhost kernel: [17179575.404000] hda: cache flushes supported
Apr 23 09:58:52 localhost kernel: [17179575.404000]  hda: hda1
Apr 23 09:58:52 localhost kernel: [17179575.412000] hdb: max request size: 128KiB
Apr 23 09:58:52 localhost kernel: [17179575.412000] hdb: 19541088 sectors (10005 MB) w/512KiB Cache, CHS=19386/16/63, UDMA(66)
Apr 23 09:58:52 localhost kernel: [17179575.416000] hdb: cache flushes not supported
Apr 23 09:58:52 localhost kernel: [17179575.416000]  hdb: hdb1 hdb2 < hdb5 >
Apr 23 09:58:52 localhost kernel: [17179575.448000] **hdd: max request size: 128KiB**
Apr 23 09:58:52 localhost kernel: [17179575.448000] **hdd: 40132503 sectors (20547 MB) w/1819KiB Cache, CHS=39813/16/63, UDMA(133)**
Apr 23 09:58:52 localhost kernel: [17179575.448000] hdc: ATAPI 40X CD-ROM drive, 128kB Cache
Apr 23 09:58:52 localhost kernel: [17179575.448000] Uniform CD-ROM driver Revision: 3.20
Apr 23 09:58:52 localhost kernel: [17179575.448000] **hdd: cache flushes supported**
Apr 23 09:58:52 localhost kernel: [17179575.448000]  **hdd:<4>hdd: dma_timer_expiry: dma status == 0x61**
Apr 23 09:58:52 localhost kernel: [17179605.448000] **hdd: DMA timeout error**
Apr 23 09:58:52 localhost kernel: [17179605.448000] **hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }**
Apr 23 09:58:52 localhost kernel: [17179605.448000] **ide: failed opcode was: unknown**
Apr 23 09:58:52 localhost kernel: [17179605.448000] hdc: status error: status=0x51 { DriveReady SeekComplete Error }
Apr 23 09:58:52 localhost kernel: [17179605.448000] hdc: status error: error=0x04 { AbortedCommand }
Apr 23 09:58:52 localhost kernel: [17179605.448000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179605.448000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Apr 23 09:58:52 localhost kernel: [17179605.448000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179605.448000] hdc: drive not ready for command
Apr 23 09:58:52 localhost kernel: [17179610.452000] hdc: status timeout: status=0xd0 { Busy }
Apr 23 09:58:52 localhost kernel: [17179610.452000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179610.452000] hdc: DMA disabled
Apr 23 09:58:52 localhost kernel: [17179610.452000] hdc: drive not ready for command
Apr 23 09:58:52 localhost kernel: [17179610.500000] hdc: ATAPI reset complete
Apr 23 09:58:52 localhost kernel: [17179610.700000]  hdd1
Apr 23 09:58:52 localhost kernel: [17179630.716000] **hdd: dma_timer_expiry: dma status == 0x41**
Apr 23 09:58:52 localhost kernel: [17179640.716000] **hdd: DMA timeout error**
Apr 23 09:58:52 localhost kernel: [17179640.716000] **hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }**
Apr 23 09:58:52 localhost kernel: [17179640.716000] **ide: failed opcode was: unknown**
Apr 23 09:58:52 localhost kernel: [17179640.716000] hdc: status error: status=0x51 { DriveReady SeekComplete Error }
Apr 23 09:58:52 localhost kernel: [17179640.716000] hdc: status error: error=0x04 { AbortedCommand }
Apr 23 09:58:52 localhost kernel: [17179640.716000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179640.716000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Apr 23 09:58:52 localhost kernel: [17179640.716000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179640.716000] hdc: drive not ready for command
Apr 23 09:58:52 localhost kernel: [17179645.720000] hdc: status timeout: status=0xd0 { Busy }
Apr 23 09:58:52 localhost kernel: [17179645.720000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179645.720000] hdc: drive not ready for command
Apr 23 09:58:52 localhost kernel: [17179645.768000] hdc: ATAPI reset complete
Apr 23 09:58:52 localhost kernel: [17179665.968000] **hdd: dma_timer_expiry: dma status == 0x41**
Apr 23 09:58:52 localhost kernel: [17179675.968000] **hdd: DMA timeout error**
Apr 23 09:58:52 localhost kernel: [17179675.968000] **hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }**
Apr 23 09:58:52 localhost kernel: [17179675.968000] **ide: failed opcode was: unknown**
Apr 23 09:58:52 localhost kernel: [17179675.968000] hdc: status error: status=0x51 { DriveReady SeekComplete Error }
Apr 23 09:58:52 localhost kernel: [17179675.968000] hdc: status error: error=0x04 { AbortedCommand }
Apr 23 09:58:52 localhost kernel: [17179675.968000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179675.968000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Apr 23 09:58:52 localhost kernel: [17179675.968000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179675.968000] hdc: drive not ready for command
Apr 23 09:58:52 localhost kernel: [17179680.972000] hdc: status timeout: status=0xd0 { Busy }
Apr 23 09:58:52 localhost kernel: [17179680.972000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179680.972000] hdc: drive not ready for command
Apr 23 09:58:52 localhost kernel: [17179681.020000] hdc: ATAPI reset complete
Apr 23 09:58:52 localhost kernel: [17179701.220000] **hdd: dma_timer_expiry: dma status == 0x41**
Apr 23 09:58:52 localhost kernel: [17179711.220000] **hdd: DMA timeout error**
Apr 23 09:58:52 localhost kernel: [17179711.220000] **hdd: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }**
Apr 23 09:58:52 localhost kernel: [17179711.220000] **ide: failed opcode was: unknown**
Apr 23 09:58:52 localhost kernel: [17179711.220000] hdc: status error: status=0x51 { DriveReady SeekComplete Error }
Apr 23 09:58:52 localhost kernel: [17179711.220000] hdc: status error: error=0x04 { AbortedCommand }
Apr 23 09:58:52 localhost kernel: [17179711.220000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179711.220000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Apr 23 09:58:52 localhost kernel: [17179711.220000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179711.220000] hdc: drive not ready for command
Apr 23 09:58:52 localhost kernel: [17179716.224000] hdc: status timeout: status=0xd0 { Busy }
Apr 23 09:58:52 localhost kernel: [17179716.224000] ide: failed opcode was: unknown
Apr 23 09:58:52 localhost kernel: [17179716.224000] hdc: drive not ready for command
Apr 23 09:58:52 localhost kernel: [17179716.272000] hdc: ATAPI reset complete

```

Any ideas ?
What exactly is the change you made ?

Thanks in advance.

---

### Post by pablovp on 2007-04-24
Removed the hda line from /etc/hdparm.conf and added it to /etc/init.d/bootmisc.sh.

---

### Post by cygnus81 on 2007-04-24
> **pablovp said:**
> Removed the hda line from /etc/hdparm.conf and added it to /etc/init.d/bootmisc.sh.

Except for a "quiet" line, my /etc/hdparam.conf file is all commented out, and                          I don't quite understand where to add that line (simply "hda"?) in /etc/init.d/bootmisc.sh .
Also, I tried to `man` both filenames to understand exactly what they do, but found nothing.
Can you explain in short what they are there for, what they do? Especially hdparam.conf.

Sorry for the newbieness.

---

### Post by Cimmo on 2007-10-24
> **cygnus81 said:**
> Except for a "quiet" line, my /etc/hdparam.conf file is all commented out, and                          I don't quite understand where to add that line (simply "hda"?) in /etc/init.d/bootmisc.sh .
Also, I tried to `man` both filenames to understand exactly what they do, but found nothing.
Can you explain in short what they are there for, what they do? Especially hdparam.conf.

Sorry for the newbieness.

yeah I confirm, I have the same problem on Gutsy with an old hard disk,however in hdparam.conf all is commented (only quite isn't) and in the other file I really cannot understand where to put and what to put inside, some tips will be apprecited.

thanx

---


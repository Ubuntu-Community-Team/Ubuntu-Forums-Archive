---
title: "Please help me diagnose possible hard disk failing"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by Captain Rotundo on 2007-09-17
I had a crash last night (the system became unresponsive) after a reset during boot a
scan was done on one of my partitions because it was flagged as having errors.
The scan (I've now done a couple) always finishes and everthing looks ok, but once I start writing to the disk (using pretty much anything) the system ends up remounting the disk read only due to trouble (which basically causes a need to hard reset the machine since the desktop becomes severely unresponsive if you suddenly make home read-only on it.  this seems to be the important info from my syslog: - is this symptomatic of a impending hard disk failure (as of now I have moved my home directories to another partition and have this one mounted ro, but this partition with the trouble is on the same disk as my root partition) or some other trouble?

Thanks in advance for any advice.

Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: EH in ADMA mode, notifier 0x0 notifier_error 0x0 gen_ctl 0x1501000 status 0x400 next cpb count 0x0 next cpb idx 0x0
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: CPB 0: ctl_flags 0x1f, resp_flags 0x2
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: CPB 1: ctl_flags 0x1f, resp_flags 0x2
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: CPB 2: ctl_flags 0x1f, resp_flags 0x2
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: CPB 3: ctl_flags 0x1f, resp_flags 0x2
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: CPB 4: ctl_flags 0x1f, resp_flags 0x2
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: CPB 5: ctl_flags 0x1f, resp_flags 0x2
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: CPB 16: ctl_flags 0x1f, resp_flags 0x2
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: CPB 29: ctl_flags 0x1f, resp_flags 0x2
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: CPB 30: ctl_flags 0x1f, resp_flags 0x2
Sep 17 09:00:58 penelope kernel: [  170.144000] ata4: timeout waiting for ADMA IDLE, stat=0x400Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: exception Emask 0x0 SAct 0x6001003f SErr 0x0 action 0x2 frozen Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: cmd 61/e8:00:5f:e7:fd/01:00:2d:00:00/40 tag 0 cdb 0x0 data 249856 out
Sep 17 09:00:58 penelope kernel: [  170.144000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: cmd 61/e8:08:47:e9:fd/01:00:2d:00:00/40 tag 1 cdb 0x0 data 249856 out
Sep 17 09:00:58 penelope kernel: [  170.144000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: cmd 61/e8:10:07:e2:fd/01:00:2d:00:00/40 tag 2 cdb 0x0 data 249856 out
Sep 17 09:00:58 penelope kernel: [  170.144000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: cmd 61/20:18:df:77:fd/00:00:2d:00:00/40 tag 3 cdb 0x0 data 16384 out
Sep 17 09:00:58 penelope kernel: [  170.144000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: cmd 61/e8:20:37:de:fd/01:00:2d:00:00/40 tag 4 cdb 0x0 data 249856 out
Sep 17 09:00:58 penelope kernel: [  170.144000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: cmd 61/98:28:2f:eb:fd/00:00:2d:00:00/40 tag 5 cdb 0x0 data 77824 out
Sep 17 09:00:58 penelope kernel: [  170.144000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: cmd 61/e8:80:1f:e0:fd/01:00:2d:00:00/40 tag 16 cdb 0x0 data 249856 out
Sep 17 09:00:58 penelope kernel: [  170.144000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: cmd 61/e8:e8:3f:26:fc/01:00:2d:00:00/40 tag 29 cdb 0x0 data 249856 out
Sep 17 09:00:58 penelope kernel: [  170.144000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)Sep 17 09:00:58 penelope kernel: [  170.144000] ata4.00: cmd 61/e8:f0:27:28:fc/01:00:2d:00:00/40 tag 30 cdb 0x0 data 249856 out
Sep 17 09:00:58 penelope kernel: [  170.144000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 17 09:00:58 penelope kernel: [  170.456000] ata4: soft resetting port
Sep 17 09:00:58 penelope kernel: [  170.612000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Sep 17 09:00:58 penelope kernel: [  170.624000] ATA: abnormal status 0xC0 on port 0xf893e59c
Sep 17 09:00:58 penelope kernel: [  170.632000] ATA: abnormal status 0xC0 on port 0xf893e59c
Sep 17 09:00:58 penelope last message repeated 4 times
Sep 17 09:01:28 penelope kernel: [  200.644000] ata4.00: qc timeout (cmd 0xec)
Sep 17 09:01:28 penelope kernel: [  200.644000] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 17 09:01:28 penelope kernel: [  200.644000] ata4.00: revalidation failed (errno=-5)
Sep 17 09:01:28 penelope kernel: [  200.644000] ata4: failed to recover some devices, retrying in 5 secs
Sep 17 09:01:33 penelope kernel: [  205.648000] ata4: hard resetting port
Sep 17 09:01:41 penelope kernel: [  213.128000] ata4: port is slow to respond, please be patient (Status 0x80)

---


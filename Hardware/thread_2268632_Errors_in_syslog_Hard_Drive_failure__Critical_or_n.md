---
title: "Errors in syslog: Hard Drive failure?  Critical or not?"
date: 2015-03-10
forum: Hardware
---

### Post by peridian on 2015-03-10
Hi,

I noticed the following errors in a syslog on a server this morning.  They look like hard drive issues.  The system is up and running, all drives are mounted and all data being accessed.  There are no errors in smartctl.

Are these critical or have the drives automatically corrected the issue?

Regards,
Rob.

```

Mar 10 06:34:02 hostname kernel: [46001.747151] ata4.00: exception Emask 0x10 SAct 0x7e0 SErr 0x400100 action 0x6 frozen
Mar 10 06:34:02 hostname kernel: [46001.747177] ata4.00: irq_stat 0x08000000, interface fatal error
Mar 10 06:34:02 hostname kernel: [46001.747195] ata4: SError: { UnrecovData Handshk }
Mar 10 06:34:02 hostname kernel: [46001.747209] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:02 hostname kernel: [46001.747226] ata4.00: cmd 61/00:28:48:c3:33/04:00:0c:00:00/40 tag 5 ncq 524288 out
Mar 10 06:34:02 hostname kernel: [46001.747226]          res 40/00:54:48:d7:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:02 hostname kernel: [46001.747266] ata4.00: status: { DRDY }
Mar 10 06:34:02 hostname kernel: [46001.747276] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:02 hostname kernel: [46001.747292] ata4.00: cmd 61/00:30:48:c7:33/04:00:0c:00:00/40 tag 6 ncq 524288 out
Mar 10 06:34:02 hostname kernel: [46001.747292]          res 40/00:54:48:d7:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:02 hostname kernel: [46001.747333] ata4.00: status: { DRDY }
Mar 10 06:34:02 hostname kernel: [46001.747343] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:02 hostname kernel: [46001.747359] ata4.00: cmd 61/00:38:48:cb:33/04:00:0c:00:00/40 tag 7 ncq 524288 out
Mar 10 06:34:02 hostname kernel: [46001.747359]          res 40/00:54:48:d7:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:02 hostname kernel: [46001.747399] ata4.00: status: { DRDY }
Mar 10 06:34:02 hostname kernel: [46001.747409] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:02 hostname kernel: [46001.747425] ata4.00: cmd 61/00:40:48:cf:33/04:00:0c:00:00/40 tag 8 ncq 524288 out
Mar 10 06:34:02 hostname kernel: [46001.747425]          res 40/00:54:48:d7:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:02 hostname kernel: [46001.747465] ata4.00: status: { DRDY }
Mar 10 06:34:02 hostname kernel: [46001.747476] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:02 hostname kernel: [46001.747491]          res 40/00:54:48:d7:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:02 hostname kernel: [46001.747531] ata4.00: status: { DRDY }
Mar 10 06:34:02 hostname kernel: [46001.748156] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:02 hostname kernel: [46001.748786] ata4.00: cmd 61/70:50:48:d7:33/01:00:0c:00:00/40 tag 10 ncq 188416 out
Mar 10 06:34:02 hostname kernel: [46001.748786]          res 40/00:54:48:d7:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:02 hostname kernel: [46001.750129] ata4.00: status: { DRDY }
Mar 10 06:34:02 hostname kernel: [46001.750815] ata4: hard resetting link
Mar 10 06:34:03 hostname kernel: [46002.069398] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Mar 10 06:34:03 hostname kernel: [46002.070485] ata4.00: configured for UDMA/133
Mar 10 06:34:03 hostname kernel: [46002.070497] ata4: EH complete
Mar 10 06:34:21 hostname kernel: [46020.821440] ata4.00: exception Emask 0x10 SAct 0x7c000003 SErr 0x400100 action 0x6 frozen
Mar 10 06:34:21 hostname kernel: [46020.822122] ata4.00: irq_stat 0x08000000, interface fatal error
Mar 10 06:34:21 hostname kernel: [46020.822758] ata4: SError: { UnrecovData Handshk }
Mar 10 06:34:21 hostname kernel: [46020.823420] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:21 hostname kernel: [46020.824094] ata4.00: cmd 61/00:00:b8:f1:33/04:00:0c:00:00/40 tag 0 ncq 524288 out
Mar 10 06:34:21 hostname kernel: [46020.824094]          res 40/00:0c:b8:f5:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:21 hostname kernel: [46020.825353] ata4.00: status: { DRDY }
Mar 10 06:34:21 hostname kernel: [46020.825979] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:21 hostname kernel: [46020.826611] ata4.00: cmd 61/50:08:b8:f5:33/00:00:0c:00:00/40 tag 1 ncq 40960 out
Mar 10 06:34:21 hostname kernel: [46020.826611]          res 40/00:0c:b8:f5:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:21 hostname kernel: [46020.827880] ata4.00: status: { DRDY }
Mar 10 06:34:21 hostname kernel: [46020.828502] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:21 hostname kernel: [46020.829123] ata4.00: cmd 61/00:d0:c8:e0:33/04:00:0c:00:00/40 tag 26 ncq 524288 out
Mar 10 06:34:21 hostname kernel: [46020.829123]          res 40/00:0c:b8:f5:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:21 hostname kernel: [46020.830384] ata4.00: status: { DRDY }
Mar 10 06:34:21 hostname kernel: [46020.831020] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:21 hostname kernel: [46020.831650] ata4.00: cmd 61/00:d8:c8:e4:33/04:00:0c:00:00/40 tag 27 ncq 524288 out
Mar 10 06:34:21 hostname kernel: [46020.831650]          res 40/00:0c:b8:f5:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:21 hostname kernel: [46020.832915] ata4.00: status: { DRDY }
Mar 10 06:34:21 hostname kernel: [46020.833545] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:21 hostname kernel: [46020.834166] ata4.00: cmd 61/b0:e0:c8:e8:33/02:00:0c:00:00/40 tag 28 ncq 352256 out
Mar 10 06:34:21 hostname kernel: [46020.834166]          res 40/00:0c:b8:f5:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:21 hostname kernel: [46020.835423] ata4.00: status: { DRDY }
Mar 10 06:34:21 hostname kernel: [46020.836044] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:21 hostname kernel: [46020.836667] ata4.00: cmd 61/40:e8:78:eb:33/02:00:0c:00:00/40 tag 29 ncq 294912 out
Mar 10 06:34:21 hostname kernel: [46020.836667]          res 40/00:0c:b8:f5:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:22 hostname kernel: [46020.837924] ata4.00: status: { DRDY }
Mar 10 06:34:22 hostname kernel: [46020.838541] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:22 hostname kernel: [46020.839164] ata4.00: cmd 61/00:f0:b8:ed:33/04:00:0c:00:00/40 tag 30 ncq 524288 out
Mar 10 06:34:22 hostname kernel: [46020.839164]          res 40/00:0c:b8:f5:33/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:22 hostname kernel: [46020.840437] ata4.00: status: { DRDY }
Mar 10 06:34:22 hostname kernel: [46020.841063] ata4: hard resetting link
Mar 10 06:34:22 hostname kernel: [46021.159127] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Mar 10 06:34:22 hostname kernel: [46021.160254] ata4.00: configured for UDMA/133
Mar 10 06:34:22 hostname kernel: [46021.160264] ata4: EH complete
Mar 10 06:34:22 hostname kernel: [46021.181351] ata4.00: exception Emask 0x10 SAct 0xc000 SErr 0x400100 action 0x6 frozen
Mar 10 06:34:22 hostname kernel: [46021.181978] ata4.00: irq_stat 0x08000000, interface fatal error
Mar 10 06:34:22 hostname kernel: [46021.182591] ata4: SError: { UnrecovData Handshk }
Mar 10 06:34:22 hostname kernel: [46021.183209] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:22 hostname kernel: [46021.183816] ata4.00: cmd 61/00:70:d0:07:34/04:00:0c:00:00/40 tag 14 ncq 524288 out
Mar 10 06:34:22 hostname kernel: [46021.183816]          res 40/00:7c:d0:0b:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:22 hostname kernel: [46021.185053] ata4.00: status: { DRDY }
Mar 10 06:34:22 hostname kernel: [46021.185663] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:22 hostname kernel: [46021.186308] ata4.00: cmd 61/38:78:d0:0b:34/03:00:0c:00:00/40 tag 15 ncq 421888 out
Mar 10 06:34:22 hostname kernel: [46021.186308]          res 40/00:7c:d0:0b:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:22 hostname kernel: [46021.187545] ata4.00: status: { DRDY }
Mar 10 06:34:22 hostname kernel: [46021.188153] ata4: hard resetting link
Mar 10 06:34:22 hostname kernel: [46021.507013] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Mar 10 06:34:22 hostname kernel: [46021.508124] ata4.00: configured for UDMA/133
Mar 10 06:34:22 hostname kernel: [46021.508132] ata4: EH complete
Mar 10 06:34:39 hostname kernel: [46038.423979] ata4: limiting SATA link speed to 3.0 Gbps
Mar 10 06:34:39 hostname kernel: [46038.423983] ata4.00: exception Emask 0x10 SAct 0x7000007f SErr 0x400100 action 0x6 frozen
Mar 10 06:34:39 hostname kernel: [46038.424622] ata4.00: irq_stat 0x08000000, interface fatal error
Mar 10 06:34:39 hostname kernel: [46038.425287] ata4: SError: { UnrecovData Handshk }
Mar 10 06:34:39 hostname kernel: [46038.425912] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.426541] ata4.00: cmd 61/00:00:a8:34:34/04:00:0c:00:00/40 tag 0 ncq 524288 out
Mar 10 06:34:39 hostname kernel: [46038.426541]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.427784] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.428398] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.429013] ata4.00: cmd 61/60:08:a8:38:34/02:00:0c:00:00/40 tag 1 ncq 311296 out
Mar 10 06:34:39 hostname kernel: [46038.429013]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.430256] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.430870] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.431479] ata4.00: cmd 61/00:10:08:3b:34/04:00:0c:00:00/40 tag 2 ncq 524288 out
Mar 10 06:34:39 hostname kernel: [46038.431479]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.432715] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.433412] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.434027] ata4.00: cmd 61/00:18:08:3f:34/04:00:0c:00:00/40 tag 3 ncq 524288 out
Mar 10 06:34:39 hostname kernel: [46038.434027]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.435274] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.435890] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.436503] ata4.00: cmd 61/f0:20:08:43:34/01:00:0c:00:00/40 tag 4 ncq 253952 out
Mar 10 06:34:39 hostname kernel: [46038.436503]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.437747] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.438359] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.438970] ata4.00: cmd 61/00:28:f8:44:34/04:00:0c:00:00/40 tag 5 ncq 524288 out
Mar 10 06:34:39 hostname kernel: [46038.438970]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.440207] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.440820] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.441430] ata4.00: cmd 61/18:30:f8:48:34/02:00:0c:00:00/40 tag 6 ncq 274432 out
Mar 10 06:34:39 hostname kernel: [46038.441430]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.442743] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.443358] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.443969] ata4.00: cmd 61/00:e0:a8:28:34/04:00:0c:00:00/40 tag 28 ncq 524288 out
Mar 10 06:34:39 hostname kernel: [46038.443969]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.445251] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.445872] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.446482] ata4.00: cmd 61/00:e8:a8:2c:34/04:00:0c:00:00/40 tag 29 ncq 524288 out
Mar 10 06:34:39 hostname kernel: [46038.446482]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.447716] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.448331] ata4.00: failed command: WRITE FPDMA QUEUED
Mar 10 06:34:39 hostname kernel: [46038.448993] ata4.00: cmd 61/00:f0:a8:30:34/04:00:0c:00:00/40 tag 30 ncq 524288 out
Mar 10 06:34:39 hostname kernel: [46038.448993]          res 40/00:34:f8:48:34/00:00:0c:00:00/40 Emask 0x10 (ATA bus error)
Mar 10 06:34:39 hostname kernel: [46038.450225] ata4.00: status: { DRDY }
Mar 10 06:34:39 hostname kernel: [46038.450831] ata4: hard resetting link
Mar 10 06:34:39 hostname kernel: [46038.769378] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Mar 10 06:34:39 hostname kernel: [46038.770458] ata4.00: configured for UDMA/133
Mar 10 06:34:39 hostname kernel: [46038.770474] ata4: EH complete

```

---

### Post by SeijiSensei on 2015-03-10
When you see that many errors, the drive is heading for trouble.  You could backup all the material on the drive, then re-format it with fsck using the -c option to look for bad blocks and mark them to be avoided.  Depending on the size of the drive, the re-format could take at least a day, beacuse the bad block check takes quite a while.

If it were me, I'd start thinking about buying a replacement drive.

---

### Post by tgalati4 on 2015-03-10
Check the cables.  They may simply need reseating.  It could be dust that is affecting the SATA chipset on the motherboard or the SATA chipset on the disk drive.  Clean and reseat everything and watch it for a few days.  Do your backups as SeijiSensei suggested.

---

### Post by scoon on 2015-03-10
Hey there, 

I know you are running a server but on my laptop, I noticed the same errors.  These were getting generated for me as a result of the hard drive spinning down when going into sleep mode.  Are your drives spinning down?  If so, stop them from doing that and see if that changes things.  If not, run a smart test on them, assuming they are new enough to be smart enabled.

Thanks, 

Skip

---

### Post by peridian on 2015-03-10
I've discovered that just before these messages occurred, a cron job ran a script pilfered from a RedHat system.  At the end of the script, it tried to run:

```

shutdown -h -P now

```

In RedHat land, that will perform a clean shutdown, but I know from past experience that Debian systems don't respond nicely to that command.

I've changed it to the "poweroff" command, and will take a look at the logs tomorrow to see if the script performed the shutdown cleanly.

Regards,
Rob.

---

### Post by tgalati4 on 2015-03-10
That's a good catch.  You certainly want your disks to finish writing and syncing before shutdown.  Had this been a real disk problem, then you know what to check in the future.

---

### Post by peridian on 2015-03-13
Well, in the end, I had to put a forced call to "sync" before the "shutdown" command.

It seems "shutdown -P" does not actually shut the system off, but performs a reboot instead.  The "-h" option is needed to switch the system off.

Only reboot seemed to avoid these errors in the logs, shutdown always seemed to produce errors, even from a terminal.

Placing an explicit call to sync seems to stop this from happening.

Regards,
Rob.

---

### Post by tgalati4 on 2015-03-13
In a multi-theaded operating system, there are several things running at once (well, sort of).  When a shutdown is initiated, all processes are sent a termination signal.  Some processes take longer than others to shut down.  Some processes should be shut down before other processes so that you have an orderly shut down.  When everything is trying to shut down at once, every process (that needs to) is trying to perform a write to disk and that can lead to problems.

You could also create a custom shutdown script and set an alias to use that instead of *poweroff* (which is a binary) and shut down critical services first, include a sleep 10 statement, and then call *poweroff*.  That should result in a cleaner shutdown.  A forced sync gives you better timing of these writes, but may not cover all Use Cases during shutdown.

For instance if you are running Drupal (which includes Apache, mysql, php, and a bunch of other stuff), you might use the Drupal control script to stop the Drupal service first, then issue the poweroff command.  A simple shutdown means you have Apache logs that are trying to be closed out, a database server that needs to close its records, and then all the system processes racing to dump their contents to disk.  That's a bad combination.  You want a little more control over the shutdown sequence.

Normally it is not a problem.  Unless it is a problem.

---


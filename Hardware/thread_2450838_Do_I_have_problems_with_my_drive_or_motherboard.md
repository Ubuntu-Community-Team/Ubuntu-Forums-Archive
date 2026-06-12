---
title: "Do I have problems with my drive or motherboard?"
date: 2020-09-22
forum: Hardware
---

### Post by xcubanoid on 2020-09-22
Hello, everyone!
I have a ubuntu server, non-system disk is connected via SATA,  cryptsetup and BTRFS. Approximately once a month or even more, the following appears in the logs:
```

Sep 18 00:05:55 white kernel: [265985.854275] BTRFS error (device dm-1):  invalid tree nritems, bytenr=4005273206784 nritems=0 expect >0
Sep 18 00:21:43 white kernel: [266934.470251] ata2.00: failed command: WRITE FPDMA QUEUED
Sep 18 00:21:43 white kernel: [266934.470259] ata2.00: cmd 61/80:00:40:db:1b/00:00:5b:01:00/40 tag 0 ncq dma 65536 out
Sep 18 00:21:43 white kernel: [266934.470259]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 18 00:21:43 white kernel: [266934.470267] ata2.00: status: { DRDY }
Sep 18 00:21:43 white kernel: [266934.470270] ata2.00: failed command: WRITE FPDMA QUEUED
Sep 18 00:21:43 white kernel: [266934.470277] ata2.00: cmd 61/20:08:20:dc:1b/00:00:5b:01:00/40 tag 1 ncq dma 16384 out
Sep 18 00:21:43 white kernel: [266934.470277]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 18 00:22:44 white kernel: [266995.066702] ata2: softreset failed (1st FIS failed)
Sep 18 00:22:44 white kernel: [266995.066714] ata2: limiting SATA link speed to 3.0 Gbps
Sep 18 00:22:44 white kernel: [266995.066716] ata2: hard resetting link
Sep 18 00:22:49 white kernel: [267000.067524] ata2: softreset failed (1st FIS failed)
Sep 18 00:22:49 white kernel: [267000.067549] ata2: reset failed, giving up
Sep 18 00:22:49 white kernel: [267000.067560] ata2.00: disabled
Sep 18 00:22:49 white kernel: [267000.067729] ata2: EH complete
Sep 18 00:22:49 white kernel: [267000.067828] sd 1:0:0:0: [sdb] tag#29  FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 18 00:22:49 white kernel: [267000.067837] sd 1:0:0:0: [sdb] tag#29  CDB: Write(16) 8a 00 00 00 00 01 5b 1b db 00 00 00 00 20 00 00
Sep 18 00:22:49 white kernel: [267000.067842] print_req_error: I/O error, dev sdb, sector 5823519488
Sep 18 00:22:49 white kernel: [267000.067885] BTRFS error (device dm-1):  bdev /dev/mapper/private errs: wr 1, rd 0, flush 0, corrupt 0, gen 0
Sep 18 00:22:49 white kernel: [267000.067955] sd 1:0:0:0: [sdb] tag#30  FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 18 00:22:49 white kernel: [267000.067961] sd 1:0:0:0: [sdb] tag#30  CDB: Write(16) 8a 00 00 00 00 01 5b 1b 97 a0 00 00 00 a0 00 00
Sep 18 00:22:49 white kernel: [267000.067964] print_req_error: I/O error, dev sdb, sector 5823502240
Sep 18 00:22:49 white kernel: [267000.067990] BTRFS error (device dm-1):  bdev /dev/mapper/private errs: wr 2, rd 0, flush 0, corrupt 0, gen 0

```
and the partition goes into read-only mode.
SMART disk contains nothing criminal. SATA cable has been replaced. BIOS has been updated.
Do I have to change my motherboard? Or the disk?

---

### Post by TheFu on 2020-09-22
Probably the disk, but check the **SMART data** to see how much data loss has already happened. If this is an SSD, you are lucky.
Smart has 2 steps.
[LIST=1]
[*]Run a test.  sudo smartctl -t short /dev/sda
[*]Review the test results. sudo smartctl -a /dev/sda
[/LIST]

The "short" test usually takes under 5 minutes, but the command output will say how long.
A "long" test usually takes 3+ hours.  

I run short tests weekly and long tests monthly automatically. The output from each is stored for comparison for a few months using output redirection.  The change of output values over time is really where SMART is best leveraged.  If there are 20 dead sectors in a week, that's much worse than if 1 sector dies every year.

You'll need to look up each parameter that SMART shows to understand what they mean. Hot disks, error counts, relocated and pending sectors are usually the most important indicator of imminent death. When an SSD drive goes into read-only mode, that is a lucky thing screaming "REPLACE ME NOW!"  When SSDs fail, no access is possible. Get your daily/weekly backups happening ASAP!

---

### Post by scorp123 on 2020-09-22
> **xcubanoid said:**
>  and the partition goes into read-only mode.
SMART disk contains nothing criminal. SATA cable has been replaced. BIOS has been updated.
Do I have to change my motherboard? Or the disk?

I'd put my bet on the disk, based on experience. It's the most likely thing to fail due to mechanical wear and tear (assuming we're not talking about an SSD here....)

If it were the motherboard you'd experience other issues as well, e.g. you should also be getting error messages from other disk devices, you'd experience random system reboots and system freezes, Linux throwing kernel panics at you, system taking ages to boot because it somehow seems stuck on the BIOS screen, not wanting to move forward with the boot sequence, and so on...

Also: how hot does the system get? How hot does that disk get?

In my experience temperature can have strange side-effects on some harddrives, even if the temperature stays below any critical limits. I have high-speed server harddrives here where everything is running fine for as long as the disks don't go above 60° C. But these are high-speed server harddrives, so they get hot pretty quickly. And once they go beyond 60° C all kinds of strange things start happening, even though according to the manufacturer these disks should be running just fine at e.g. 70° C for as long as they are being cooled and don't get any hotter. But nope...  I get all kinds of weird error messages with these disks once they go beyond 60 ° C.

I wrote a little shell script that makes use of the "smartctl" program and checks the temperature of all disks that are present in the system:
```

#! /bin/bash
for disk in `sudo fdisk -l | grep "Disk /dev" | awk '{ print $2 }' | cut -d: -f1`;
do
      echo "Disk: "$disk
      sudo smartctl -x $disk | grep "Current Temperature:"
done
```

Example output from one of my systems:

```

> disk-tempcheck.sh

Disk: /dev/sda
Current Temperature:                    30 Celsius
Disk: /dev/sdb
Current Temperature:                    30 Celsius
Disk: /dev/sdc
Current Temperature:                    31 Celsius
Disk: /dev/sde
Current Temperature:                    30 Celsius
Disk: /dev/sdd
Current Temperature:                    31 Celsius

```

So in that server the cooling is pretty good, none of the harddrives get really hot even when this server is used 24 x 7.

Maybe check the temperature in your system too? Could be that your disk is getting a bit hot at some point and that's where it starts to act "funny" ...?

---

### Post by TheFu on 2020-09-22
Thanks for that script.  I modified it slightly when loop devices and LVM LVs showed up:
```
#! /bin/bash
for disk in `sudo fdisk -l | grep "Disk /dev" \
    | egrep -v '/dev/loop|/dev/mapper' | awk '{ print $2 }'\
    | cut -d: -f1`;
do
      echo "Disk: "$disk
      sudo smartctl -x $disk | grep "Current Temperature:"
done
```

Should be a little cleaner output.

---

### Post by xcubanoid on 2020-09-23
Thank you all for your advice. Replaced my hard drive. I am watching now. If there is any news, I will inform you here.

---

### Post by TheFu on 2020-09-23
> **xcubanoid said:**
> Thank you all for your advice. Replaced my hard drive. I am watching now. If there is any news, I will inform you here.

You replaced it without looking at the SMART data?  I wouldn't have done that.

---


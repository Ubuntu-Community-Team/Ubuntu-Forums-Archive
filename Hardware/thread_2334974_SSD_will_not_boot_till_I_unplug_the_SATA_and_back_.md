---
title: "SSD will not boot till I unplug the SATA and back in."
date: 2016-08-24
forum: Hardware
---

### Post by Raymond Day on 2016-08-24
I got a SSD as a data drive and every time when I go to reboot my Ubuntu server it will not boot saying waiting for something and then saying put in my password to go on.

I have a SSD on a USB 3.0 so it plugs right in the SATA and power on the SSD. If I do this as Ubuntu is waiting, unplug the SATA and back in then Ubuntu will boot and mount the SSD too.

This has been like this over a year now. I thought time to see if can fix it.

The dmesg message at the end looks like this:

```
[   85.690648] sd 9:0:0:0: [sde] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[   85.690845] sd 9:0:0:0: [sde] Write Protect is off
[   85.690848] sd 9:0:0:0: [sde] Mode Sense: 43 00 00 00
[   85.691045] sd 9:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   85.692616]  sde: sde1
[   85.693461] sd 9:0:0:0: [sde] Attached SCSI disk
[   85.775091] EXT4-fs (sde1): recovery complete
[   85.775095] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
[  312.313321] EXT4-fs (sda1): error count since last fsck: 7
[  312.313357] EXT4-fs (sda1): initial error at time 1440247610: ext4_journal_check_start:56
[  312.313369] EXT4-fs (sda1): last error at time 1440423823: ext4_put_super:790: inode 2
[  639.865734] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
```

Can unmounted it and do this command to test it:

```
fsck -t ext4 -p /dev/sde1
fsck from util-linux 2.27.1
256SSD: clean, 30627/15630336 files, 35812366/62514432 blocks
```

So looks like nothing is wrong.

From the dmesg can any one see what could be wrong?

-Raymond Day

---

### Post by TheFu on 2016-08-24
I've seen a similar issue and like you, haven't done much research to figure out why.

My first checks would be the boot order in the BIOS. I don't reboot that often and when I do, don't usually take the time to check on the hard-to-get-into UEFI BIOS on that box.  Last time I tried to get into the BIOS, took about 30 reboots. Yes, I know the correct key to press, but it just doesn't accept it all the time. Besides this, the box works perfectly.

Have you checked the BIOS boot order?

---


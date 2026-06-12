---
title: "Hard Disk failure, or something else?"
date: 2009-01-29
forum: Hardware
---

### Post by CrimsonRider on 2009-01-29
Hi, I've been recently running into some problems with a homebuild storage box I've been running. It's got 3 disks, 640 gb each, setup in RAID5.

Now every so often the system spontanously rebooted, and the raid array would become degraded. Checking the logs of this gave me;

```
[ 5644.520059] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5644.520087] ata3.00: cmd 35/00:00:ab:de:c7/00:04:1d:00:00/e0 tag 0 dma 524288 out
[ 5644.520089]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 5644.520117] ata3.00: status: { DRDY }
[ 5649.890024] ata3: link is slow to respond, please be patient (ready=0)
[ 5654.570024] ata3: device not ready (errno=-16), forcing hardreset
[ 5654.570036] ata3: soft resetting link
[ 5659.770024] ata3: link is slow to respond, please be patient (ready=0)
[ 5664.630028] ata3: SRST failed (errno=-16)
[ 5664.630054] ata3: soft resetting link
[ 5669.830020] ata3: link is slow to respond, please be patient (ready=0)
[ 5674.690026] ata3: SRST failed (errno=-16)
[ 5674.690052] ata3: soft resetting link
[ 5679.890023] ata3: link is slow to respond, please be patient (ready=0)
[ 5709.710027] ata3: SRST failed (errno=-16)
[ 5709.710054] ata3: limiting SATA link speed to 1.5 Gbps
[ 5709.710062] ata3: soft resetting link
[ 5714.730027] ata3: SRST failed (errno=-16)
[ 5714.730048] ata3: reset failed, giving up
[ 5714.730058] ata3.00: disabled
[ 5714.730078] ata3: EH complete
[ 5714.730142] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 5714.730148] end_request: I/O error, dev sda, sector 499637931
[ 5714.730164] raid5: Disk failure on sda2, disabling device.
[ 5714.730165] raid5: Operation continuing on 2 devices.
[ 5714.730287] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 5714.730291] end_request: I/O error, dev sda, sector 499638955
[ 5714.730351] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 5714.730355] end_request: I/O error, dev sda, sector 26394559
[ 5714.730371] end_request: I/O error, dev sda, sector 26394559
[ 5714.730383] md: super_written gets error=-5, uptodate=0
[ 5714.730387] raid1: Disk failure on sda1, disabling device.
[ 5714.730388] raid1: Operation continuing on 2 devices.
[ 5714.730418] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 5714.730421] end_request: I/O error, dev sda, sector 13698335
[ 5714.730433] raid1: sda1: rescheduling sector 13698272
```

The system comes up again, and works fine for another few hours, and then reboots again. I was thinking HD failure, but the disks have been replaced, rotated etc. But I still get the problem. Then I tought, controller issue, but the onboard controller gives the same problem as the simple Silicon Image controller. ( The SII does about 35000k/s rebuilding, the onboard does about 60000k/s )

I've done some searching, and this could be a driver/mobo problem . Anyone have any idea? Or make more sense of the log then I can?

---

### Post by electrogeist on 2009-01-29
I dunno but I'll throw a few things out there...

Did you pull the other controller card when you tested with the motherboard's integrated controller?  Disable integrated when using the add-on one?  Pull/disable all other non-essential hardware for testing?  Incl pulling cd/dvd!

Do you have the latest BIOS for your board?  I'd do this first.  I wish harddrive firmware was available for easy download too without having to request it... you can compare firmware versions between drives with  sudo hdparm -i /dev/sd_ or use a capital i

Possibly settings for PCI mapping in BIOS, or where it loads option ROMS?  If you have 4GB or more and especially running as 32-bit you could try decreasing the RAM.

SATA or IDE? (doesn't IDE now show up as /dev/sd_ too?)  If SATA does the BIOS or controller card firmware allow for a legacy mode, where it will make the drives appear as IDE?  Not optimal but if it works... And try other modes, and RAID on/off.  If IDE try cable select using the drive jumpers and correct position on the cables.

Have grub pass irqpoll at boot?

A bad cable?

You could try rolling your own minimalistic, latest kernel from kernel.org.  But it can take forever to go through and read all the options nowadays.

Also your problem looks similar to these:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256637)
2nd one they are getting: COMRESET failed (errno=-16)
while you are getting: SRST failed (errno=-16)

Good luck!

---


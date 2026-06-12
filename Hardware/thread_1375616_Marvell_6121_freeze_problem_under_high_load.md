---
title: "Marvell 6121 freeze problem under high load"
date: 2010-01-08
forum: Hardware
---

### Post by Bogo999 on 2010-01-08
I have a ASUS M3A32-MPV Deluxe MB with a Marvell 6121 secondary RAID controller on it.  It has two internal connection SATA ports on it.  When I put fast disks on the ports and exercise them with high throughputs the controller will eventually freeze and both drives will go dead.  It takes a reboot to get the ports operating again.  I'm not using the controller's own RAID hardware.  Right now I'm testing with each drive separate, but in the end I want to use the two drives along with two drives on the other SATA controller as a md RAID 5.  Anybody else run into this problem?  What was your solution?  Do I have to go to using a kernal.org kernel?  It looks like they have changed handling of the Marvell controller to provide support under the ahci driver, kernel 2.6.25.r7 and higher.  Also looks like there are a couple bugs fixed in later kernels.  I'm not a fan of running development kernels, but I did do it when I was using Debian so I know the pitfalls.  

Here are the error messages from dmesg output:
> [42458.009793] ata8.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[42458.009804] ata8.00: cmd 25/00:00:00:48:17/00:01:1d:00:00/e0 tag 0 dma 131072 in
[42458.009805]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x24 (host bus error)
[42458.009808] ata8.00: status: { DRDY }
[42458.010449] BAR5:00:FF 01:FF 02:FF 03:FF 04:FF 05:FF 06:FF 07:FF 08:FF 09:FF 0A:FF 0B:FF 0C:FF 0D:FF 0E:FF 0F:FF
[42458.011077] ata8: soft resetting link
[42488.156954] ata8.01: qc timeout (cmd 0xec)
[42488.156963] ata8.01: failed to IDENTIFY (I/O error, err_mask=0x5)
[42488.156965] ata8.01: revalidation failed (errno=-5)
[42488.156969] ata8: failed to recover some devices, retrying in 5 secs
[42493.160036] BAR5:00:FF 01:FF 02:FF 03:FF 04:FF 05:FF 06:FF 07:FF 08:FF 09:FF 0A:FF 0B:FF 0C:FF 0D:FF 0E:FF 0F:FF
[42493.160548] ata8: soft resetting link
[42523.306150] ata8.01: qc timeout (cmd 0xec)
[42523.306160] ata8.01: failed to IDENTIFY (I/O error, err_mask=0x5)
[42523.306163] ata8.01: revalidation failed (errno=-5)
[42523.306167] ata8: failed to recover some devices, retrying in 5 secs
[42528.311248] BAR5:00:FF 01:FF 02:FF 03:FF 04:FF 05:FF 06:FF 07:FF 08:FF 09:FF 0A:FF 0B:FF 0C:FF 0D:FF 0E:FF 0F:FF
[42528.311745] ata8: soft resetting link
[42558.464595] ata8.01: qc timeout (cmd 0xec)
[42558.464605] ata8.01: failed to IDENTIFY (I/O error, err_mask=0x5)
[42558.464607] ata8.01: revalidation failed (errno=-5)
[42558.464611] ata8.01: disabled
[42558.970690] ata8.00: failed to IDENTIFY (I/O error, err_mask=0x40)
[42558.970695] ata8.00: revalidation failed (errno=-5)
[42558.970698] ata8: failed to recover some devices, retrying in 5 secs
[42563.973853] BAR5:00:FF 01:FF 02:FF 03:FF 04:FF 05:FF 06:FF 07:FF 08:FF 09:FF 0A:FF 0B:FF 0C:FF 0D:FF 0E:FF 0F:FF
[42563.974429] ata8: soft resetting link
[42594.120410] ata8.00: qc timeout (cmd 0xec)
[42594.120421] ata8.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[42594.120424] ata8.00: revalidation failed (errno=-5)
[42594.120427] ata8: failed to recover some devices, retrying in 5 secs
[42599.125346] BAR5:00:FF 01:FF 02:FF 03:FF 04:FF 05:FF 06:FF 07:FF 08:FF 09:FF 0A:FF 0B:FF 0C:FF 0D:FF 0E:FF 0F:FF
[42599.125838] ata8: soft resetting link
[42629.279112] ata8.00: qc timeout (cmd 0xec)
[42629.279123] ata8.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[42629.279125] ata8.00: revalidation failed (errno=-5)
[42629.279129] ata8.00: disabled
[42629.787593] BAR5:00:FF 01:FF 02:FF 03:FF 04:FF 05:FF 06:FF 07:FF 08:FF 09:FF 0A:FF 0B:FF 0C:FF 0D:FF 0E:FF 0F:FF
[42629.788101] ata8: soft resetting link
[42629.943757] ata8: EH complete
[42629.943780] sd 7:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[42629.943784] end_request: I/O error, dev sde, sector 488065024
The operation in progress was the third iteration of "dd if=/dev/sde of=/dev/null bs=128k" in a while loop.  I can reproduce the failure and all produce similar error outputs.  It does not matter which hard disk I use.  I've tried 3 different ones, both Seagate and Western Digital, and all will fail after awhile.  Failure can happen on either channel and when it happens both channels fail.  I thought the chip may be overheating so I added a heat sink to it and put a fan on it.  No change.  It still failed.  Failures also happen under any motherboard temperature.

My release is 8.04, Hardy Heron with all patches up to date.
uname -a output:
> Linux boing 2.6.24-26-generic #1 SMP Tue Dec 1 17:55:03 UTC 2009 x86_64 GNU/Linux

---


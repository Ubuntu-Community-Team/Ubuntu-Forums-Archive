---
title: "Hard drive failure?"
date: 2008-05-27
forum: Hardware
---

### Post by Oswald1 on 2008-05-27
Hi all!

What happened that today the whole system went somehow crazy popping up all sorts of programs and what not (according to my girlfriend, as I wasn't around at the time). After a while the system froze and she hard booted it. After booting, Ubuntu said that it couldn't find the homes, which are on a separate drive and adviced to boot in recovery mode.

When booting in recovery mode it first start recovering the volume with the homes and shortly the system freezes after messages along the lines:

ata6.00: Exception Emask *some hex codes*
ata6.00: CPB resp_flags 0x11, CMD error
ata6.00: cmd *a long list of numbers* dma *number*
ata6.00: Status: ( DRDY ERR )
ata6.00> error: ( UNC )


Also, when I run from a live CD and try mounting the disk with the homes, the system completely freezes. The file system is ext3 on the problematic volume.

Yesterday I think some kernel updates were installed, but don't know if those have anything to do with anything. I was running 8.04.

Any help would be deeply appreciated. Thank god I make nightly backups :)

---

### Post by az on 2008-05-27
> **Oswald1 said:**
> Hi all!

What happened that today the whole system went somehow crazy popping up all sorts of programs and what not (according to my girlfriend, as I wasn't around at the time). After a while the system froze and she hard booted it. After booting, Ubuntu said that it couldn't find the homes, which are on a separate drive and adviced to boot in recovery mode.

When booting in recovery mode it first start recovering the volume with the homes and shortly the system freezes after messages along the lines:

ata6.00: Exception Emask *some hex codes*
ata6.00: CPB resp_flags 0x11, CMD error
ata6.00: cmd *a long list of numbers* dma *number*
ata6.00: Status: ( DRDY ERR )
ata6.00> error: ( UNC )


Also, when I run from a live CD and try mounting the disk with the homes, the system completely freezes. The file system is ext3 on the problematic volume.

Yesterday I think some kernel updates were installed, but don't know if those have anything to do with anything. I was running 8.04.

Any help would be deeply appreciated. Thank god I make nightly backups :)

It sounds like your drive is broken.  If you need to recover files from the dead drive, try gnu ddrescue.  See

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org) 
or
[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)


I would not try to fix the broken drive.  It will never be reliable.  Just pull any data you need off it (if you can) and get a new one.

---

### Post by Oswald1 on 2008-05-27
Ok, thanks. That kinda sucks but luckily I have backups and warranty should be in effect for the drive as well.

Is there some reliable way to test if it really is a hardware failure? I have pretty bad experiences dealing with warranty issues and such if I cannot show that the device really is malfunctioning.

---

### Post by az on 2008-05-29
> **Oswald1 said:**
> Ok, thanks. That kinda sucks but luckily I have backups and warranty should be in effect for the drive as well.

Is there some reliable way to test if it really is a hardware failure? I have pretty bad experiences dealing with warranty issues and such if I cannot show that the device really is malfunctioning.

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

Use S.m.a.r.t.

---


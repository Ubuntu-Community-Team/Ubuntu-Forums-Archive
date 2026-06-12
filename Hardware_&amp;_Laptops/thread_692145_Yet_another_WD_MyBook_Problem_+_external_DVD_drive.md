---
title: "Yet another WD MyBook Problem + external DVD drive"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by scearley on 2008-02-09
I have a 500GB MyBook on NTFS.  I want to use this effectively between XP and Kubuntu on my dual-boot.  However, The drive does not automount in k no matter what I do.

In fact, not only will it not automount, but the only way I can get it to mount is to boot with it plugged in (either USB or FIrewire), then once the system is booted, remove the connection plug, then plug it in to USB.  The times I've tried to get this connected with Firewire have never worked.

Needless to say this is ridiculously frustrating.

[FONT="Courier New"]lsusb[/FONT] returns this before the "cord-swap":
```

Bus 003 Device 004: ID 4855:4288
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp.
Bus 001 Device 001: ID 0000:0000

```

and this after:

```

Bus 003 Device 005: ID 1058:0903 Western Digital Technologies, Inc.
Bus 003 Device 004: ID 4855:4288
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp.
Bus 001 Device 001: ID 0000:0000

```

so I'm obviously not imagining the drive not being available, or otherwise 'hiding' in some way that I'm not aware of.

That said, I have exactly the same problems with my external DVD, except it is **not** showing up after the [FONT="Courier New"]lsusb[/FONT] command, even though putting in a CD or a DVD results in the system detecting the disk (once I've gone through the boot/unplug/plug sequence I have to go through with the HDD). WHat makes it even more bewildering (for me, at least) is that I'm able to read and view everything on the CD/DVD through Dolphin.

The only advice I've been able to find involves disconnecting through WIndows on shutdown.  I've been doing this, and to no avail.  But in any case, that doesn't really explain the DVD problem.

Any directions I should go?

---


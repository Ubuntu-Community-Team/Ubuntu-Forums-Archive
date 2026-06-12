---
title: "SMART, hdparm, and the external USB hard drive"
date: 2009-10-13
forum: Hardware
---

### Post by nfirvine on 2009-10-13
I've got an Eee PC 701 that I'm using as a light fileserver.  Naturally, it's got an external USB hard drive hanging off it all the time.  Problem is, it only really gets used occasionally (weekly backups), and doesn't really need to be on all the time.  But it never even spins down, which I thought SMART or something would cover.

If I run smartctl against the drive, it reports that the drive doesn't support SMART.  And if I try a hdparm -y or -Y, it replies with:
```

/dev/sdb:
 issuing standby command
 HDIO_DRIVE_CMD(standby) failed: Input/output error

```

So I wonder... is it that USB to SATA (externally powered, 3.5in, FYI) adaptors in general don't do SMART/hdparm, or just this particular one?  Perhaps the hardware supports it, but the drivers don't?

Cheers.

---

### Post by dandnsmith on 2009-10-13
Whatever it is you want, I don't think SMART is the thing, as that is aimed at recording and reporting problems with the drive

[wiki article](http://en.wikipedia.org/wiki/S.M.A.R.T.)

There might be an interfacing issue when doing the SATA to usb - it might just not be supported, but I don't know as I've never had to try it

---


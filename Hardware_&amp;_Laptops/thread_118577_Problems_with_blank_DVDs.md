---
title: "Problems with blank DVDs"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by kwisatz on 2006-01-17
I bought some days ago some blank dvds, I put one of them into my dvd burner (on my HP laptop) and then I can see on my dmesg:

[4299021.637000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4299021.637000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299021.637000] ide: failed opcode was: unknown
[4299021.637000] end_request: I/O error, dev hdc, sector 0
[4299021.637000] Buffer I/O error on device hdc, logical block 0
[4299021.640000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4299021.640000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299021.640000] ide: failed opcode was: unknown
[4299021.640000] end_request: I/O error, dev hdc, sector 0
[4299021.640000] Buffer I/O error on device hdc, logical block 0
[4299021.783000] attempt to access beyond end of device
[4299021.783000] hdc: rw=0, want=68, limit=4
[4299021.783000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16


And no automount, I tried to manually mount my dvd but:
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I don't know what to do, in the past I burned some dvds...maybe it's a problem of THIS brand of blank dvds?

Thank you in advance,

---

### Post by radiazo on 2006-01-17
what dvd's are??? samsung??? I have a external lg dvd burner and the same problem... only with the samsung plextomax dvds... with memorex, verbatim or princo i have no problem. maybe a incompatible medium.

---

### Post by StefanoCole on 2006-01-18
kwisatz, first a trivial question: are you sure the format (-R, +R, -RW, +RW) of the DVDs you bought is supported by your burner? I mean, if your burner only supports DVD+R you cannot use it to burn DVD-R.
Second, even if it supports a specific format, lets say DVD-R, it is possible that the burner won't be compatible with a particular DVD-R brand. In some cases the burner manufacturer may issue an upgrade of the firmware to allow the burner to detect new DVD media brands. You can check if this is your case.

Hope this helps, Stefano

---

### Post by kwisatz on 2006-01-24
Yesterday I tried with a DVD-RW that in the past I wrote perfectly but It didn't work...
I have a breezy with backports, maybe a udev problem?
Any ideas?

thank you

PS: My DVD-Burner can burn DVD-R, +R e +RW...

---


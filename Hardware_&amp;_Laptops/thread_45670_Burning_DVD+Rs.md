---
title: "Burning DVD+Rs?"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by robbie1 on 2005-07-01
See Horay Hedgehog Hardware Help..


I have been useing Gnomebaker/growisofs/Graveman to burn DVD+Rs which seems to burn correctly (visible on the dvd) but when trying to mount one I just burnt I get the following error:

> Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superbloack on /dev/hdc missing codepage or other error 

When using growisofs I get:

/dev/hdc: "Current Write Speed" is 8.2x1385KBps.
:-? the LUN appears to be stuck writing LBA=310h, retry in 70ms
:-? the LUN appears to be stuck writing LBA=310h, retry in 70ms

And the dvd is unreadable.

Is there anything I have to do to enable DVD burning? Device manager lists the device as "PIONEER DVD-RW DVR-109" and it is +/- compatible.

Cheers, 

rob

Below is a tail of my dmesg:

UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
eth0: no IPv6 routers present
eth0: no IPv6 routers present
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
cdrom: This disc doesn't have any tracks I recognize!
cdrom: This disc doesn't have any tracks I recognize!
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8294400, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293376, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293152, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8294392, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293368, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293144, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293800, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8292776, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8292552, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8293792, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8292768, limit=4
attempt to access beyond end of device
hdc: rw=0, want=8292544, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6805668, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804644, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804420, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6805660, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804636, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804412, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6805068, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804044, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6803820, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6805060, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6804036, limit=4
attempt to access beyond end of device
hdc: rw=0, want=6803812, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1252, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1028, limit=4
UDF-fs: No partition found (1)
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
cdrom: This disc doesn't have any tracks I recognize!

---

### Post by kassetra on 2005-09-13
This issue has also been reported in the current Hoary forums - please see the Hoary Hardware help for more information.

---

### Post by az on 2005-09-13
[http://ubuntuforums.org/showthread.php?t=24605](http://ubuntuforums.org/showthread.php?t=24605)

---


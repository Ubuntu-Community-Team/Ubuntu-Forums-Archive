---
title: "EXT HD used to work in Ubuntu Jaunty, but now it  does not mount."
date: 2009-10-22
forum: Hardware
---

### Post by oceano10000 on 2009-10-22
It used to mount, but recently its been giving me this: 

> $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Fixed it, used ntfs tools to fix it.

---

### Post by Dark_Stang on 2009-10-22
Yum. Windows filesystem errors.

---


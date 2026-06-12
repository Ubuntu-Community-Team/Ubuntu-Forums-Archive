---
title: "Iomega External HD won't mount"
date: 2011-07-20
forum: Hardware
---

### Post by ryanchang on 2011-07-20
Hey there,

I'm having an issue with my Iomega 1TB External HDD not mounting on my Ubuntu 10.10. It was just plugged into a MacBook Pro w/10.6.7 running, and now I'm getting the following error message:

> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

If anyone could shed some light on this and help me out that would be greatly appreciated! 

Thanks
ryan

---


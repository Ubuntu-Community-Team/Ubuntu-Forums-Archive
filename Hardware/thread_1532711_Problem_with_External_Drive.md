---
title: "Problem with External Drive"
date: 2010-07-16
forum: Hardware
---

### Post by guy.komaclo on 2010-07-16
I got the following problem.
I was copying some data from one of my partition to my external HD and accidently I 
unplugged my external HD during the copying time now I received the following message.

Could you help, please?

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by efflandt on 2010-07-17
So have you tried doing what the error tells you to, run **chkdsk /f** on that partition from a Windows box?

That worked from a USB enclosure for a laptop drive that refused to boot WinXP due to bad sectors, or another time when it got corrupted by a virus (not mine, just fixing it for someone).  Although, it may not work if there is significant physical damage (like dropping the drive, especially while running).

---

### Post by IcarusR on 2010-07-17
Or if you have an windows cd you can boot from that & use recovery console to run chkdsk.

---

### Post by AltomineUK on 2010-07-17
Like the others.....try to run chkdisk from a windows box.

---


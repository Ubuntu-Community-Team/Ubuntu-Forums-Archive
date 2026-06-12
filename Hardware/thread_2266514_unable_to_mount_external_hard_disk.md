---
title: "unable to mount external hard disk"
date: 2015-02-23
forum: Hardware
---

### Post by dhia2 on 2015-02-23
Hi, 

I was using a ubuntu live cd to backup data from a laptop to an external hard disk of 1Tb. suddently i removed the HD wire.
Then, when i tried to plug it again, i got an error message:
[HTML]Error mounting /dev/sdb1 at /media/SP PHD U3: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/SP PHD U3"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.[/HTML]

Even when i try to read it on Windows system, it seams reading indefinitely, then i got an empty hard disk.

How can i solve this problem ?
Thanks in advance

---

### Post by leclerc65 on 2015-02-23
Did you try as suggested 
  'In the first case run chkdsk /f on Windows...'  ?

---

### Post by dhia2 on 2015-02-23
> **leclerc65 said:**
> Did you try as suggested 
  'In the first case run chkdsk /f on Windows...'  ?

Hi,

Thanks for your advise.
I just did it. It worked for the first HD (as they are two in fact) and i'm still trying to get it working for the second.

---


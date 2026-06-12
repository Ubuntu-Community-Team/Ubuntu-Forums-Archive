---
title: "mount drive"
date: 2010-11-10
forum: Hardware
---

### Post by machacaz on 2010-11-10
Hi.
I had an external drive that a friend give me to repair - its his sister external hard drive.e 
the main user uses it on windows. 
I run a few tests on it and indicates several errors. 

my first ideia was to try to mount it on ubuntu, get data and send it to repair.
on windows the disk isn't recognized and on ubuntu 
i tried to forcede to mount: 

*sudo ntfs-3g /dev/sdb1 /media/disco -o force*

i got this error message:

[I]ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read $MFTMirr: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.[/I]

can someone give orientations from this point?

---


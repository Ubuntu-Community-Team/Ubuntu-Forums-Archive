---
title: "Unable to Mount"
date: 2009-12-26
forum: Hardware
---

### Post by seriousfix on 2009-12-26
I get the following errors when I try to mount the second partition on my secondary drive:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb5': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

HPFS/NTFS 0x7 /dev/sdb5

Odd thing is that it is partition 5 on a disc with only 2 partitions.

Please let me know what I can do to fix this.

Thanks,

tss

---

### Post by taurus on 2009-12-26
Do you have windows on that machine (dualboot with Ubuntu)?  Boot into windows and run a check disk on that partition to make sure everything is good with it.  And please remember to shut down windows cleanly instead of using a short cut for shutting it down.

p.s.  Maybe you only have two partitions on that drive but at least one of them is an extended partition, /dev/sdb5.

---

### Post by seriousfix on 2009-12-28
I had Windows on the drive Ubuntu is on now.  No more windows on this PC at this time.  I really don't want to use it.  Maybe I can swap a hard drive, install windows, fix the disc and see if that works.

Thank you for the advice.

Is this the only way to get it working?

Thanks again.

tss

---


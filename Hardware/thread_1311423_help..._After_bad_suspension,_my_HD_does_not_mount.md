---
title: "help... After bad suspension, my HD does not mount in ubuntu 9.10 - it does in Win"
date: 2009-11-02
forum: Hardware
---

### Post by dario_it_81 on 2009-11-02
Hi everyone,

yesterday my notebook went into suspension and never came back... there was an HD mounted. Now it says:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

The HD gets mounted in Win XP. I am worried about doing a chkdsk /F... I did the chkdsk read-only, and it finds some errors in one file.

What do I do, in order to be safe?

Thx,
Dario

---

### Post by aquamammal on 2009-11-16
Same problem. Anyone?

---

### Post by joshmuffin on 2010-02-12
Bump

---


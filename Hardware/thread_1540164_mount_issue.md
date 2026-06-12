---
title: "mount issue"
date: 2010-07-27
forum: Hardware
---

### Post by @atreya on 2010-07-27
Every time i try to mount a partition of mine the following message crops up

WHAT TO DO..??


Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: Zero run length: Input/output error
ntfs_attr_pread_i: Failed to find VCN #1: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

am a pure newbie...so please... 
need to solve this asap as most of my work data are stored there..??

---

### Post by IcarusR on 2010-07-27
If you have access to a windows box plug it in to it & run chkdsk.
Or boot from XP cd & use recovery console to run chkdsk.

This has resolved this issue for others who have had same error.

---

### Post by @atreya on 2010-07-27
but i am moving a lot these days so i cant get hold of  windows cd...any way of getting it done within ubuntu..??

---


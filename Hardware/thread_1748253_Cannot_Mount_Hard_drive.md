---
title: "Cannot Mount Hard drive"
date: 2011-05-03
forum: Hardware
---

### Post by TheClint93 on 2011-05-03
My External HDD (samsung 640GB) cannot be mounted

It shows the following error.


Unable to mount SAMSUNG


Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


What am i supposed to do?

---

### Post by IcarusR on 2011-05-03
Try plugging it into a windows box & run chkdsk on it as recommended in the error.

---

### Post by TheClint93 on 2011-05-03
Isnt there anything i can do on Ubuntu. i dont have windows.

---

### Post by IcarusR on 2011-05-04
You could try running ntfsfix & ntfsck, but I believe they are very limited in what errors they can fix.
Do you use this drive on windows at all ? If not I would strongly recommend backing it up & reformatting as ext4 which you can manage under ubuntu.
Chkdsk really is the best way to fix problems on ntfs, can you use a friends windows box ?
If you search the forum for this problem you will find other threads with give same advise.

---


---
title: "Error mounting external hdd - random auto umount"
date: 2012-04-18
forum: Hardware
---

### Post by parovelb on 2012-04-18
I have an external LC Power housing with a 80Gb WD eide disk. When connecting it to the right side of my Lenovo Ideapad s205 (it has issues with the right side usb ports) it gives me an error after a while.     Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).  Failed to mount '/dev/sdd1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware.  In the first case run chkdsk /f on Windows then reboot into Windows twice.  The usage of the /f parameter is very important!  If the device is a SoftRAID/FakeRAID then first activate iit and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1).  Please see the 'dmraid' documentation for more details.      Any ideas?

---


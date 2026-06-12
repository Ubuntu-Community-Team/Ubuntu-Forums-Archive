---
title: "External NTFS Formated Drive will not mount"
date: 2011-03-18
forum: Hardware
---

### Post by Vince N on 2011-03-18
Hey all,

I have an external Seagate HardDrive formatted for NTFS.  Since yesterday I have not been able to load it in Ubuntu with the error message 

> **Unable to mount Seagate External Drive**


Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x315b6250  size: 1024  usa_ofs: 60739  usa_count: 50137: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x601c39b8  size: 1024  usa_ofs: 41090  usa_count: 11573: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x5795d840  size: 1024  usa_ofs: 37094  usa_count: 2965: Invalid argument
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I performed the requested instructions.  The drive mounts and reads fine in windows.  Any help?

---


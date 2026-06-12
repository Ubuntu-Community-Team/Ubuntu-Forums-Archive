---
title: "Error mounting: mount exited with exit code 13"
date: 2012-02-13
forum: Hardware
---

### Post by Penguinion on 2012-02-13
Hey! Wasn't sure where to post this, but this felt right.

So I just started my computer one day with Windows XP and couldn't visualize my fourth harddrive, the first works, the second is not visible as it's completely installed with ubuntu, and the third seems to work. In ubuntu I can at least see my harddrive but when I try to mount it through a double click through the computer, I eventually get this message, and then the harddrive is gone.
> 
Error mounting: mount exited with exit code 13: The disk contains an unclean file system (0, 1).
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
Failed to sync device /dev/sdc1: Input/output error
Failed to close volume /dev/sdc1: Input/output errorI've read around a little but my unique problem is that I can't spot my disk, I also ran the command "sudo fdisk -l" and it wasn't there either >_<'.

It would be really nice to get some help, I don't want to loose anything out of that disk, either.

I'm gonna try to reboot and see what's happening, but thanks, and sorry if I wasn't informative enough.

---

### Post by Penguinion on 2012-02-17
bump

---


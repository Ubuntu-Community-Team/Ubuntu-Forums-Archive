---
title: "Hard Drive wont Mount"
date: 2010-09-24
forum: Hardware
---

### Post by TimEnid on 2010-09-24
I was in the middle of transferring files to a Buffalo usb 3.0 external and it just cut off on me. I restarted my pc and clicked on the drive and i get this message:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdn1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

can i get some help, thanks. It was running fine for the past couple of weeks. I hope its not dead. I didnt have much on it.

---

### Post by TimEnid on 2010-09-24
got it fixed. just followed the instruction in this link, in case anyone else experiences this.
[http://ubuntuforums.org/archive/index.php/t-1333205.html](http://ubuntuforums.org/archive/index.php/t-1333205.html)

---


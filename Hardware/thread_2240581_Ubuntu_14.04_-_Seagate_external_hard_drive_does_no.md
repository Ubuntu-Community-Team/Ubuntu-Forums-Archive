---
title: "Ubuntu 14.04 - Seagate external hard drive does not mount"
date: 2014-08-21
forum: Hardware
---

### Post by tatianeps2 on 2014-08-21
I have an external hard drive that was working fine, in fact it has all my backups.

But now it throws this error when I connect it to any USB ports. The same error happens on two machines I've tested and it will probably happen on any other machine.

This is the error:
```
Error mounting /dev/sdc1 at /media/tatianeps/tps-1tb-hd: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdc1" "/media/tatianeps/tps-1tb-hd"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

[ATTACH=CONFIG]255684[/ATTACH]

I really hope this is something simple to fix that I might be missing here. I don't have any Windows machine around to run chkdsk as the error message suggests.
I'm in despair because this external drive has all my backup files. Please help. :confused:

Edit:
The last thing I remember is to use this external drive to backup a 7.7 GB tar.gz. I always use Ubuntu's option to safely remove it. 
And the hard drive didn't fall, it did not happen any kind of accident with it.

Edit  [2]:
I've got to a computer with Windows and it opens the drive. I can browse my files, move, copy, ... whatever I try on Windows is just fine. But on Ubuntu, the same error happens when I try to mount the external drive. I need to fix it, because the things I have backed up are from using Ubuntu.

Edit [3]:
Please forgive my rush to solve the issue. I could not see what was right in front of me. After I run chkdsk /f on Windows, whatever was broken was fixed.
I never though that, after all, Windows would come to rescue. Topic is solved. =P

---


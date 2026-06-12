---
title: "Problem with second SATA drive"
date: 2010-11-25
forum: Hardware
---

### Post by thehumanproject on 2010-11-25
Hi, I have two Hdd's which one I use for my OS and the second one for storage. Well today, I tried mounting my second HDD and it gave me this error:

> Error mounting: mount exited with exit code 13: Error reading bootsector: Input/output error
Failed to sync device /dev/sdb1: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
I don't have windows so how do I fix my HDD?

---

### Post by Fafler on 2010-11-25
Install the package ntfsprogs and try ntfsfix. I don't know if it can work together with badblocks in case the drive has bad blocks.

---

### Post by thehumanproject on 2010-11-25
> root@Tardis:~# ntfsfix /dev/sdb
Failed to determine whether /dev/sdb is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.


It says there is no directory, but that is the directory of my second hdd. Now what?

---

### Post by Fafler on 2010-11-25
Nope, it's /dev/sdb1. /dev/sdb is the raw device ;)

---

### Post by thehumanproject on 2010-11-25
> root@Tardis:~# ntfsfix /dev/sdb1
Failed to determine whether /dev/sdb1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.


I'm not sure what to do anymore.

---

### Post by Fafler on 2010-11-25
Can  you read it with dd?

```
dd if=/dev/sdb1 of=/dev/null bs=1M count=10
```

If it works without errors the drive is okay and the filesystem is fscked. In that case, you'll need to find a Windows machine. Or use VirtualBox and install Windows on top.

If it fails, the drive is broken. In that case, i'd try GetDataBack for NTFS. And you'll still need Windows.

Why do you, by the way, keep your data on a NTFS drive when you doesn't use Windows?

---

### Post by dandnsmith on 2010-11-25
I'd start with
*fdisk -l*
to show the partition table contents.
This will show whether the system thinks there is a second HDD, and clues as to what might be on it.
If it (effectively) says there is no 2nd HDD,
then you need to check things - first see if the BIOS is registering it on bootup.

---


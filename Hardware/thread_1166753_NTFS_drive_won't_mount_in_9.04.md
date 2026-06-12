---
title: "NTFS drive won't mount in 9.04"
date: 2009-05-22
forum: Hardware
---

### Post by Ncc Tardis on 2009-05-22
My NTFS drive won't mount, I either get the 

"                                                             DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending"

or the

" You are not privileged to mount this drive "

The icon exists in the Computer section of the File Browser, and it recognises and has mounted my Windows XP ntfs drive, but refuses to mount this one

I only created this setup within the past 24 hours, installing XP home in the first partition, Ubuntu in the second, a Swap partition, and the remaining 200gb in another ntfs partition for media, etc.

Is there any way to fix this?
Or
Are there any file systems that both OSes will read/write to natively?

EDIT:
This is what I'm trying in Terminal... is it the correct code?

ncctardis@Pana-laptop-U:~$ sudo mount /dev/sda4 /media/Data
[sudo] password for ncctardis: 
ntfs_mst_post_read_fixup: Invalid argument
ntfs_mst_post_read_fixup: Invalid argument
ntfs_mst_post_read_fixup: Invalid argument
ntfs_mst_post_read_fixup: Invalid argument
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda4': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ncctardis@Pana-laptop-U:~$

---

### Post by renzokuken on 2009-05-22
the code you are using in the terminal is the right idea but lacking some flags to tell it that its an ntfs filesystem.


have you tried using the ntfs-config package to mount the drive with full read/write permissions?

```
sudo apt-get install ntfs-config
```

and then go to System - Admin (might be the other one, cant remember offhand) and use the NTFS-Config app to easily mount your drive. it will make it a permanent mount (add it to your fstab file) with full read/write permission

---


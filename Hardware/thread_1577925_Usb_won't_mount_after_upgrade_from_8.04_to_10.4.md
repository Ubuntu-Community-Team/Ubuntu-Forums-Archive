---
title: "Usb won't mount after upgrade from 8.04 to 10.4"
date: 2010-09-19
forum: Hardware
---

### Post by murpjf88 on 2010-09-19
I can't mount my usb drive since upgrading from 8.04 to 10.04. I have tried 

> sudo apt-get install ntfsprogs

Which was installed, then

> sudo ntfsfix /dev/sdb1

The message I got was this

> Failed to determine whether /dev/sdb1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

Sometimes I get this message when I first put the drive in.

> DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

About a minute later, I receive this one.

> Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read $AttrDef, unexpected length (-1 != 2560).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Not sure what any of this means, but there is nothing wrong with the drives. I have 4 external hard drives and I receive the same message from all of them. On the other hand, sometimes it doesn't even recognize the hard drive at all. Any help would be appreciated.

---

### Post by WinRiddance on 2010-11-15
I definitely feel your pain ...
Identical problem as yours and can't get anyone knowledgeable enough to help with this. 

Even used the "eject safely" option in the disk utility, followed by taking the disk (it's a Samsung) to a friend's windows computer. But since he only has WindowsVista (with extended privileges requiring permission), I wasn't able to use the chkdsk /f option. No permission to perform said function. The drive is recognized everywhere and there's no doubt in my mind that it's still a good drive since I only used it for backup purposes ... very infrequently ... so it's exactly this kind of thing, amongst many other little things, that keeps Ubuntu away from many "scared" Windows, Mac, and other users. It's hard for me to believe that there isn't a readily available, easy to understand fix for this ... considering how many people have been posting similar problems ...
Hard to believe that there isn't an UBUNTU easy fix for this !!! What are people who have no access to Windows supposed to do in such a situation?** Very frustrating** ... :mad:

---


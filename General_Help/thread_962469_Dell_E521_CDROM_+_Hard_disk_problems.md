---
title: "Dell E521 CDROM + Hard disk problems"
date: 2008-10-29
forum: General Help
---

### Post by towersoft on 2008-10-29
Hi,
    I have just installed Ubuntu hardy on a Dell Dimension E521 and am having problems with its secondary hard disk and CDROM drives.

CDROM - The computer has 2 Drives and even when there is no disk present it flashes the read light every 2 seconds or so. This is not a problem in itself until you open the drive to put a cd in. The tray will then just get sucked back into the drive within a couple of seconds. Great way to scratch Cd's. 

Second Hard disk - I have formatted this to EXT3 and hoped it would mount with no problems, however it does not. All I get from the drive is " DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." If I then try and format the disk again through gparted I get: 
"mkfs.ext3 /dev/sdb1

mke2fs 1.40.8 (13-Mar-2008)
/dev/sdb1 is apparently in use by the system; will not make filesystem here!"

This machine has NVIDIA raid but I have switched it off in the BIOS. I have also updated the BIOS to its most recent revision. Any help would be appreciated as I am searching around and cant seem to find anything that completely applies to either problem. Thanks in advance!.

    Phil

---


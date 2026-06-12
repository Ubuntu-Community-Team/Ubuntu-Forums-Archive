---
title: "The infamous mount drive issue"
date: 2008-08-06
forum: Hardware
---

### Post by Tiken on 2008-08-06
I'm going to do my best to lay this out as neatly and sensibly as possible
so that anyone else that experiences this problem may be able to follow it and use any fixes provided to help them too.

I'm quite new to Ubuntu so I apologize if I don't catch on first try, but I will do my best to explain what is going on and give as much information needed

Ok.
So I'm using Hardy Heron and have tried connecting a Seagate 500gig external.
" error org .freedesktop.dbus.error.access denied "

I followed some other forum posts seeing there was a fix that would work for me, after trying a few I DO now have it pop up saying 
" Opening Free Agent Drive " but it is shortly followed by 

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. "



I tested the drive in another machine and it works fine.
Ive tried the sudo ntfsfix /dev/sdb1 command
to which it said " Mounting volume . . . OK "

It still didnt work so I tried ( sudo fdisk -l )


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64186418

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

And got that, so then I saw it had the disk I wanted to mount as /dev/sdb
so I tried 

"sudo ntfsfix /dev/sdb"

" Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.":confused:

Help would be greatly appreciated.

I apologize if thats too much / not enough information.
I don't to get scolded :P

---

### Post by jdelaender on 2008-08-18
Hi

similar problem here.

I'm working on a Transtec PC, trying to mount an external hard drive (HDDrive2GO from Medion).

After boot up, I get an error message:
Cannot mount volume, Error org.freedesktop.DBus.Error.AccessDenied.

A security policy in place prevents this sender from sending this message to the recepient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume"  member "Mount" error name "(unset)" destination "org.freedesktop.Hal"

The mount doesn't want to work with the automatic ubuntu feature, however, mounting the drive manually works correctly, and also makes the hard drive icon on the ubuntu desktop appear and work correctly.

Still I would like to find out how to make the automount in ubuntu working...

Any help appreciated!

---


---
title: "Input/output error when attepmting to mount hard drive"
date: 2011-03-30
forum: Hardware
---

### Post by Jabrouwer on 2011-03-30
The windows partition (the only partition) seems to be corrupted, and i can't boot into it.

I've booted from my Linux Mint live cd, but I get errors whenever i try to mount the partition.  From the GUI, it opens an error window: "Unable to mount location Dbus error org.gtk.Private.RemoteVolumeMonitor.Failed: And Operation is already pending"  then another window pops up saying "Unable to mount location, DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.  Pssible causes include: the remote application did not send a reply, the message bus security blocked the reply, the reply timeout expired, or the network connection was broken."

Running the following in the terminal:

```
mkdir /media/disk
mount -t ntfs-3g /dev/sda3 /media/disk -o force
```

gives two errors :
```
Failed to write lock '/dev/sda3': Resource temporarily unavailable
Error opening '/dev/sda3': Resource temporarily unavailable
Failed to mount '/dev/sda3': Resource temporarily unavailable
```

and

```
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware.  In the first case run chkdsk /f on Windows
the reboot into Windows twice.  The usage of the /f parameter is very important!  If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
```

It isn't RAID, and I can't run chkdsk on windows since I can't boot into windows.

also, gparted give an Input/output error.

Any ideas on how to get into the windows partition?

---

### Post by Jabrouwer on 2011-03-30
It now gives the second error repeatedly

---

### Post by Perfect Storm on 2011-03-30
Hi Jabrouwer

There's a Linux Mint forum to get help with your distro.
You'll find it here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


regards
A.I. Dude
Ubuntu Forum Staff

---


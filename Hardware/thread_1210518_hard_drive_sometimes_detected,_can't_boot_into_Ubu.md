---
title: "hard drive sometimes detected, can't boot into Ubuntu"
date: 2009-07-11
forum: Hardware
---

### Post by brynjarh on 2009-07-11
*EDIT* Think I'll just use [GNU ddrescue]("https://help.ubuntu.com/community/DataRecovery#Data%20Recovery%20from%20damaged%20filesystem%20or%20drive") *EDIT*

My hard drive is acting funky.

When I set down in front of my computer today there was nothing but black and the mouse, so I rebooted.

When I boot up the computer either finds the hard drive or not, when it does not find it I get "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"

When it does find it I usually get to "GRUB loading, please wait..." and then get "Error 17".

If I boot using a Live CD and the hard drive was found the partitions show up in Places>Computer, but when I try to access/open one of them I get: "Cannot mount volume. Unable to mount volume. mount: wrong fs type, bad option, bad superblock on /dev/sda4, missing codepage or helper program, or other error    In some cases useful info is found in syslog - try dmesg | tail or so."

After awhile another message pops up: "Unable to mount location   DBus error org.freedesktop.DBus.Error.NoReplay: Did not receive a replay. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired or the network connection was broken."

Taking the advice of the first message, running dmesg | tail I get:

```
[  759.540390] sd 3:0:0:0: [sda] Add. Sense: Address mark not found for data field
[  759.540397] end_request: I/O error, dev sda, sector 537044280
[  759.540424] ata4: EH complete
[  759.540441] JBD: Failed to read block at offset 25459
[  759.540447] JBD: recovery failed
[  759.540449] EXT3-fs: error loading journal.
[  759.540467] sd 3:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[  759.540489] sd 3:0:0:0: [sda] Write Protect is off
[  759.540492] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  759.540529] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Opening up Gparted either ends in no device being found or it's found, showing all the partitions, when I right click one and select Check I eventually get all this:

```
GParted 0.4.3

Libparted 1.8.8
Check and repair file system (ext3) on /dev/sda2  00:00:56    ( ERROR )
     	
calibrate /dev/sda2  00:00:04    ( SUCCESS )
     	
path: /dev/sda2
start: 491910300
end: 530964314
size: 39054015 (18.62 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:52    ( ERROR )
     	
e2fsck -f -y -v /dev/sda2
     	
/dev/sda2: recovering journal
JBD: Failed to read block at offset 5459
JBD: IO error -5 recovering block 5459 in log
JBD: Failed to read block at offset 5460
JBD: IO error -5 recovering block 5460 in log
JBD: Failed to read block at offset 5461
JBD: IO error -5 recovering block 5461 in log
JBD: Failed to read block at offset 5462
JBD: IO error -5 recovering block 5462 in log
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda2: Attempt to read block from filesystem resulted in short read while reading block 2398044

/dev/sda2: Attempt to read block from filesystem resulted in short read while reading block 2398045

/dev/sda2: Attempt to read block from filesystem resulted in short read while reading block 2398046

/dev/sda2: Attempt to read block from filesystem resulted in short read while reading block 2398047

e2fsck: Input/output error while recovering ext3 journal of /dev/sda2

========================================
```


I also notice there are no folders in /media/.

Any ideas what is wrong and what I could do?

---


---
title: "SD Card wont mount after standby - EXT4 - Help!"
date: 2009-04-19
forum: Hardware
---

### Post by sammcj on 2009-04-19
I've got myself in some trouble here.

I'm on an **HP Mini 1004TU.**
**Running /var/cache/apt on a SD card** to save space.

I know the flash card is ok and I'm sure I've had this problem before:

Just came out of standby and noticed my flash drive wasnt showing on the desktop...

Took the card out and put it back in '**You are not privileged to mount this volume**'

So I go into the console and try to mount **as root - 'Wrong FS type, bad option, bad superblock on /dev/sdb**1' etc etc...

**dmesg** gives me:
[sdb] attached scsi removeable disk
attached scsi generic sgl type 0
EXT4-fs: no journal found

[I]The flash card is ext4 and is mounted with defaults,exec,rw,noatime.
[/I]

---


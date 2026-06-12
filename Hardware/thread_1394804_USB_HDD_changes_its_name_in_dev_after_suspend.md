---
title: "USB HDD changes its name in /dev/ after suspend"
date: 2010-01-31
forum: Hardware
---

### Post by alexalecu on 2010-01-31
My USB storage device is permanently connected to my laptop and has 2 partitions: the first one is a regular one formatted as ext4, while the 2nd is a LUKS encrypted partition.

Here's the relevant entries in /etc/crypttab
```
sdb2		/dev/disk/by-uuid/06363c7f-39e9-41d4-ac47-2680949b54e7		none		luks
```

and the ones from /etc/fstab
```
# /dev/sdb1
UUID=46284f80-b4d7-46d6-abdf-4341ff90a3c1		/media/backup	ext4		defaults,relatime		0	2
/dev/mapper/sdb2					/media/sdb2	ext4		defaults,relatime,bootwait	0	2

```

When the system starts up, both partition get auto-mounted correctly.

But, after resuming from suspend, sdb (along with sdb1 and sdb2) disappears from /dev/ and 3 new entry are created: sdc, sdc1 and sdc2.
The system tries to auto-mount sdc1 and it fails with the following message (displayed in a popup dialog):
```
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /media/backup
mount failed
```
It also tries to auto-mount sdc2 and it asks me for the password.

dmesg gives the following message about the USB device after resume (nothing related to sdb though)
```
[ 1056.800186] usb-storage: device scan complete
[ 1056.842613] scsi 3:0:0:0: Direct-Access     ST950032 5AS                   PQ: 0 ANSI: 2 CCS
[ 1056.843453] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1056.853102] sd 3:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 1056.853895] sd 3:0:0:0: [sdc] Write Protect is off
[ 1056.853901] sd 3:0:0:0: [sdc] Mode Sense: 28 00 00 00
[ 1056.853906] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 1056.855390] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 1056.855398]  sdc: sdc1 sdc2
[ 1056.922298] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[ 1056.922307] sd 3:0:0:0: [sdc] Attached SCSI disk
```

I've been trying to find a fix to this problem, but all similar reports are old and they got fixed by setting the USB persist mode to 1 for that device in /sys/bus/usb/devices/.../power/persist. I've checked my file and it contains 1, but still the persist mode doesn't work.

---

### Post by alexalecu on 2010-02-02
Anyone ? I would appreciate any suggestion, as I have ran out of ideas here.

---

### Post by baustromverteiler on 2010-09-06
hi,

check

[http://ubuntuforums.org/showpost.php?p=9813382](http://ubuntuforums.org/showpost.php?p=9813382)

and see if mounting by UUID and the script works for you.

---


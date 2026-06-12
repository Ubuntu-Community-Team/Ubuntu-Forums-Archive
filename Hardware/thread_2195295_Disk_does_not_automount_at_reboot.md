---
title: "Disk does not automount at reboot"
date: 2013-12-23
forum: Hardware
---

### Post by cle-ziskind on 2013-12-23
... despite being in /etc/fstab:

/dev/sdb                /u                      ext3    defaults        0 0

#dmesg|less

[...]
SCSI device sdb: 286749480 512-byte hdwr sectors (146816 MB)
sdb: Write Protect is off
sdb: Mode Sense: b3 00 10 08
SCSI device sdb: write cache: disabled, read cache: enabled, supports DPO and FUA
SCSI device sdb: 286749480 512-byte hdwr sectors (146816 MB)
sdb: Write Protect is off
sdb: Mode Sense: b3 00 10 08
SCSI device sdb: write cache: disabled, read cache: enabled, supports DPO and FUA
 sdb: unknown partition table
sd 0:0:1:0: Attached scsi disk sdb


... but it mounts flawlessly, manually:

# mount /dev/sdb /u
#

Anyone care to hazard a guess why?

---

### Post by Bucky Ball on 2013-12-23
sdb is a whole drive, not a partition. You should be mounting sdb1 or whatever to /u. Why /u??? Not convention. You should be mounting it to /mnt/u or /media/u. 

You should also use the UUID to mount it. Other way raw and old (you should find your other EXT* entries in /fstab use the UUID syntax, unless you are using a very old release. Much more reliable with UUID. Could you post what you have in /fstab already, please?

If you actually make a partition on that drive, say sdb1, with drive plugged in, in terminal do:

```
sudo blkid
```

Look for sdb1. You will see 'UUID="10adng0ahga" or some other number. Save that number minus the quote marks. Open /fstab in another terminal with:

```
sudo nano /etc/fstab
```

Add this at end:

```
# Entry for sdb1
UUID=10adng0ahga  /media/u   ext3    errors=remount-ro       0       1
```

... where 10adng0ahga is the UUID you found and /media/u is where you are mounting the partition. Reboot and see if it mounts. If it doesn't, comment that line out in /fstab for now with a # tag, like so:

```
# Entry for sdb1
# UUID=10adng0ahga  /media/u   ext3    errors=remount-ro       0       1
```

If you want to be super safe, make a backup of the /fstab before you start, just in case:

```
sudo cp /etc/fstab /etc/fstab.backup
```

You will, of course, need to create the mount point in /media or wherever before any of this:

```
sudo mkdir /media/u
```

BTW, what release are you using? Just wondering why ext3 and not 4 ...

---


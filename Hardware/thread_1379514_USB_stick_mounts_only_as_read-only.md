---
title: "USB stick mounts only as read-only"
date: 2010-01-12
forum: Hardware
---

### Post by kuby on 2010-01-12
When plugging in a usb-stick, it is detected. In Kubuntu 9.10 I can mount (as user) using the Device Notifier. In Ubuntu Netbook Remix 9.10 it is automounted.

Output of mount:
```
/dev/sdd1 on /media/TOSHIBA type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
```

where rw means read-write access.

```
ls -al
drwxr-xr-x 28 kuby root  24K 1970-01-01 01:00 TOSHIBA
```

so user kuby has read-write access to directory TOSHIBA (which is the stick).

But,
**I cannot write to this USB-stick.**:(

```
kuby@kubuntu:/media/TOSHIBA$ touch test.txt
touch: cannot touch `test.txt': Read-only file system

```

Part of the problem is shown in output of ```
cat /proc/mounts
/dev/sdd1 /media/TOSHIBA vfat ro,nosuid,nodev,relatime,uid=1000,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro 0 0

```

where ro indicated read-only. But how this is set to readonly, I have no clue. 

I used a debian-live CD to verify the USB-stick itself and in Debian-live write-access worked.

Remounting as rw, makes the USB stick writeable.
```
sudo mount /dev/sdd1 -o remount,rw
```
but unplugging and plugging in again doesn't.

I don understand this behaviour and I don't like remounting an USB stick everytime I use it.
Does someone have a clue, or is it a bug?

---

### Post by boot_sectorz on 2010-01-14
Having the same problem here. What could be going wrong?

---

### Post by kuby on 2010-01-20
In /var/log/syslog I found the following entries:

```

Jan 18 06:24:04 kuby-laptop kernel: [  142.256105] usb 1-3: new high speed USB device using ehci_hcd and address 4
Jan 18 06:24:04 kuby-laptop kernel: [  142.391696] usb 1-3: configuration #1 chosen from 1 choice
Jan 18 06:24:04 kuby-laptop kernel: [  142.483114] Initializing USB Mass Storage driver...
Jan 18 06:24:04 kuby-laptop kernel: [  142.485295] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 18 06:24:04 kuby-laptop kernel: [  142.485701] usbcore: registered new interface driver usb-storage
Jan 18 06:24:04 kuby-laptop kernel: [  142.485713] USB Mass Storage support registered.
Jan 18 06:24:04 kuby-laptop kernel: [  142.486948] usb-storage: device found at 4
Jan 18 06:24:04 kuby-laptop kernel: [  142.486957] usb-storage: waiting for device to settle before scanning
Jan 18 06:24:09 kuby-laptop kernel: [  147.484403] usb-storage: device scan complete
Jan 18 06:24:09 kuby-laptop kernel: [  147.521254] scsi 4:0:0:0: Direct-Access     TOSHIBA  TransMemory      PMAP PQ: 0 ANS$
Jan 18 06:24:09 kuby-laptop kernel: [  147.524138] sd 4:0:0:0: Attached scsi generic sg1 type 0
Jan 18 06:24:10 kuby-laptop kernel: [  147.948827] sd 4:0:0:0: [sdb] 15687680 512-byte logical blocks: (8.03 GB/7.48 GiB)
Jan 18 06:24:10 kuby-laptop kernel: [  147.950316] sd 4:0:0:0: [sdb] Write Protect is off
Jan 18 06:24:10 kuby-laptop kernel: [  147.950336] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jan 18 06:24:10 kuby-laptop kernel: [  147.950351] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jan 18 06:24:10 kuby-laptop kernel: [  147.963200] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jan 18 06:24:10 kuby-laptop kernel: [  147.963223]  sdb: sdb1
Jan 18 06:24:10 kuby-laptop kernel: [  147.999576] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jan 18 06:24:10 kuby-laptop kernel: [  147.999605] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 18 06:24:14 kuby-laptop kernel: [  152.157203] FAT: Filesystem error (dev sdb1)
Jan 18 06:24:14 kuby-laptop kernel: [  152.157216]     invalid access to FAT (entry 0x367569c7)
Jan 18 06:24:14 kuby-laptop kernel: [  152.157227]     File system has been set read-only
Jan 18 06:24:14 kuby-laptop kernel: [  152.161626] FAT: Filesystem error (dev sdb1)
Jan 18 06:24:14 kuby-laptop kernel: [  152.161639]     invalid access to FAT (entry 0x156b79d0)

```

So I concluded ubuntu discovered an error with the filesystem and set the stick to readonly. I don't know why, but in Windows I could use the stick without problems, maybe the linux kernel is more strict. I executed a filesystem check (in windows, but could probably also have been done in ubuntu) and since I can read/write to this stick in ubuntu as well.

---


---
title: "Is there anything that can rediscover installed devices without reboot?"
date: 2010-12-19
forum: Hardware
---

### Post by dakra137 on 2010-12-19
With 10.04, occasionally the DVDRW drive on my HP dv7t disappears after days or weeks of working fine. After rebooting it's back.
I would call that a Microsoft style work around.

Is there anything that can cause the system to scan for installed devices and reactivate them?

Is there an equivalent to ifup and ifdown for nonnetwork devices? 

BTW, here is the udevadm output from when it is working fine:

userid@machine:~$ [COLOR="Blue"][SIZE="2"]**sudo udevadm info --query=all --name=/dev/sr0**[/SIZE][/COLOR]
P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sr0
N: sr0
S: block/11:0
S: scd0
S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0
S: cdrom
S: cdrw
S: dvd
S: dvdrw
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sr0
E: MAJOR=11
E: MINOR=0
E: DEVNAME=/dev/sr0
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: ID_CDROM=1
E: ID_CDROM_CD=1
E: ID_CDROM_CD_R=1
E: ID_CDROM_CD_RW=1
E: ID_CDROM_DVD=1
E: ID_CDROM_DVD_R=1
E: ID_CDROM_DVD_RW=1
E: ID_CDROM_DVD_RAM=1
E: ID_CDROM_DVD_PLUS_R=1
E: ID_CDROM_DVD_PLUS_RW=1
E: ID_CDROM_DVD_PLUS_R_DL=1
E: ID_SCSI=1
E: ID_VENDOR=hp
E: ID_VENDOR_ENC=hp\x20\x20\x20\x20\x20\x20
E: ID_MODEL=DVD_RW_AD-7581S
E: ID_MODEL_ENC=DVD\x20RW\x20AD-7581S\x20
E: ID_REVISION=4H73
E: ID_TYPE=cd
E: ID_BUS=scsi
E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
E: ACL_MANAGE=1
E: GENERATED=1
E: UDISKS_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/11:0 /dev/scd0 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0 /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw

---


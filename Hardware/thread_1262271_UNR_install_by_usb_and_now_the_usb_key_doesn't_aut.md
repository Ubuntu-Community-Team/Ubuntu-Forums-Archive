---
title: "UNR install by usb and now the usb key doesn't automount properly"
date: 2009-09-09
forum: Hardware
---

### Post by vegetto721 on 2009-09-09
Hi,
I installed Ubuntu netbook remix on my Samsung n120 via usb (using syslinux and copying the contents of livecd over, etc.). When I insert my usb stick, it cannot mount. From dmesg (included below), it seems to believe my usb key as being a cdrom (probably because the install was via usb but from the live cd image). I can use fstab to allow it to mount manually but I'd rather fix it so hal(?) can automount it.

```
[ 6691.488144] usb 1-6: new high speed USB device using ehci_hcd and address 4
[ 6691.622084] usb 1-6: configuration #1 chosen from 1 choice
[ 6693.237626] Initializing USB Mass Storage driver...
[ 6693.240586] scsi2 : SCSI emulation for USB Mass Storage devices
[ 6693.242128] usb-storage: device found at 4
[ 6693.242140] usb-storage: waiting for device to settle before scanning
[ 6693.242200] usbcore: registered new interface driver usb-storage
[ 6693.242216] USB Mass Storage support registered.
[ 6698.240752] usb-storage: device scan complete
[ 6698.241500] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[ 6698.242110] scsi 2:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[ 6698.247259] sd 2:0:0:0: [sdb] 1994385 512-byte hardware sectors: (1.02 GB/973 MiB)
[ 6698.247961] sd 2:0:0:0: [sdb] Write Protect is off
[ 6698.247980] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 6698.247994] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 6698.255842] sd 2:0:0:0: [sdb] 1994385 512-byte hardware sectors: (1.02 GB/973 MiB)
[ 6698.256458] sd 2:0:0:0: [sdb] Write Protect is off
[ 6698.256476] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 6698.256490] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 6698.256513]  sdb: sdb1
[ 6698.288831] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 6698.289177] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 6698.297731] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 6698.297751] Uniform CD-ROM driver Revision: 3.20
[ 6698.298199] sr 2:0:0:1: Attached scsi CD-ROM sr0
[ 6698.298504] sr 2:0:0:1: Attached scsi generic sg2 type 5
```

---

### Post by davidryderuk on 2009-09-10
Hi,
You probably have to do the following.

1. Open terminal and type the following command.

```
sudo gedit /etc/fstab
```

2. The fstab configuration file should open in gedit. You should find a line with your usb sticks address and a cd mounting point like shown below.

```
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

3. Comment the line and save your changes to fstab.

```
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

4. Hopefully your usb stick should now mount.

---

### Post by vegetto721 on 2009-09-11
Nope. I only have my root partition, swap space, and proc inside fstab.

---


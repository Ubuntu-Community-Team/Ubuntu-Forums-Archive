---
title: "SD card FSTAB entry UUID not working"
date: 2009-09-04
forum: Hardware
---

### Post by Berduchwal on 2009-09-04
I have 16Gb SD card made by Veho.
Once the card is mounted it is read only.

I have tried various fstab entries with no success. I think there might be something wrong with the card.

Some times when entry in fstab is not correct it mounts ok in read and write mode!

ls /dev/disk/by-uuid/ -alh
```
lrwxrwxrwx 1 root root  10 2009-09-04 07:37 A140-1E7E -> ../../sdc1
```

blkid - does not show the card either mounted nor unmounted

tail -f /var/log/messages

```
Sep  4 07:42:45 skrybaLtd-laptop kernel: [  501.444075] usb 1-4: new high speed USB device using ehci_hcd and address 5
Sep  4 07:42:45 skrybaLtd-laptop kernel: [  501.612378] usb 1-4: configuration #1 chosen from 1 choice
Sep  4 07:42:45 skrybaLtd-laptop kernel: [  501.654900] scsi9 : SCSI emulation for USB Mass Storage devices
Sep  4 07:42:50 skrybaLtd-laptop kernel: [  506.657135] scsi 9:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
Sep  4 07:42:51 skrybaLtd-laptop kernel: [  507.472166] sd 9:0:0:0: [sdb] 31776768 512-byte hardware sectors: (16.2 GB/15.1 GiB)
Sep  4 07:42:51 skrybaLtd-laptop kernel: [  507.473143] sd 9:0:0:0: [sdb] Write Protect is off
Sep  4 07:42:51 skrybaLtd-laptop kernel: [  507.478393] sd 9:0:0:0: [sdb] 31776768 512-byte hardware sectors: (16.2 GB/15.1 GiB)
Sep  4 07:42:51 skrybaLtd-laptop kernel: [  507.479378] sd 9:0:0:0: [sdb] Write Protect is off
Sep  4 07:42:51 skrybaLtd-laptop kernel: [  507.479397]  sdb: sdb1
Sep  4 07:42:51 skrybaLtd-laptop kernel: [  507.481507] sd 9:0:0:0: [sdb] Attached SCSI removable disk
Sep  4 07:42:51 skrybaLtd-laptop kernel: [  507.481632] sd 9:0:0:0: Attached scsi generic sg2 type 0

```

fstab
```
UUID=A140-1E7E	/media/Veho16	vfat	auto,rw	0	0
```

ls -l (of /media)
```
drwxr-xr-x 3 root root 8192 1970-01-01 01:00 Veho16
```

Can some point me what to try out next please?

---


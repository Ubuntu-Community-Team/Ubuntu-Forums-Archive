---
title: "Format information missed in sata HDD after data writing"
date: 2012-10-13
forum: Hardware
---

### Post by Dr Berta on 2012-10-13
Hi all,
I'm experiencing the following problem:
I bought a cabinet Advance model BX-3801STB for 3.5" HDD sata to usb. The disk used is a 500GB Seagate barracuda 7200.11 with firmware updated.
The problem is that it is impossible to format the HDD from ubuntu. Only with Windows XP this can be done.
When I'm under linux, if I try to store any data in the disk I loose the format informations and I have to format again the disk.
I tried using a manhattan sata to usb converter and everything worked properly.

Is there anyone that can suggest me what to do to fix the problem?

Thanks

---

### Post by Dr Berta on 2012-11-01
Update. 
I found that the cabinet works using a sata bridge Super Top M6116. 
I verified that it is impossible to format the HDD through that component.

Does anyone know if it is supported by ubuntu 12.04?

Bye

---

### Post by Dr Berta on 2012-11-03
syslog gives this message when it cannot mount the hdd
```
Nov  3 16:38:59 Gandalf kernel: [ 7592.848104] usb 3-1: new high-speed USB device number 3 using ehci_hcd
Nov  3 16:38:59 Gandalf mtp-probe: checking bus 3, device 3: "/sys/devices/pci0000:00/0000:00:16.2/usb3/3-1"
Nov  3 16:38:59 Gandalf mtp-probe: bus: 3, device: 3 was not an MTP device
Nov  3 16:39:00 Gandalf kernel: [ 7593.243129] scsi11 : usb-storage 3-1:1.0
Nov  3 16:39:00 Gandalf kernel: [ 7593.243405] usbcore: registered new interface driver ums-cypress
Nov  3 16:39:01 Gandalf kernel: [ 7594.241062] scsi 11:0:0:0: Direct-Access        Mass  Storage Device        PQ: 0 ANSI: 0
Nov  3 16:39:01 Gandalf kernel: [ 7594.242667] sd 11:0:0:0: Attached scsi generic sg9 type 0
Nov  3 16:39:01 Gandalf kernel: [ 7594.243532] sd 11:0:0:0: [sdi] 976773166 512-byte logical blocks: (500 GB/465 GiB)
Nov  3 16:39:01 Gandalf kernel: [ 7594.244131] sd 11:0:0:0: [sdi] Write Protect is off
Nov  3 16:39:01 Gandalf kernel: [ 7594.244140] sd 11:0:0:0: [sdi] Mode Sense: 03 00 00 00
Nov  3 16:39:01 Gandalf kernel: [ 7594.246810] sd 11:0:0:0: [sdi] No Caching mode page present
Nov  3 16:39:01 Gandalf kernel: [ 7594.246820] sd 11:0:0:0: [sdi] Assuming drive cache: write through
Nov  3 16:39:01 Gandalf kernel: [ 7594.250271] sd 11:0:0:0: [sdi] No Caching mode page present
Nov  3 16:39:01 Gandalf kernel: [ 7594.250280] sd 11:0:0:0: [sdi] Assuming drive cache: write through
Nov  3 16:39:01 Gandalf kernel: [ 7594.269296]  sdi: sdi1
Nov  3 16:39:01 Gandalf kernel: [ 7594.272392] sd 11:0:0:0: [sdi] No Caching mode page present
Nov  3 16:39:01 Gandalf kernel: [ 7594.272401] sd 11:0:0:0: [sdi] Assuming drive cache: write through
Nov  3 16:39:01 Gandalf kernel: [ 7594.272408] sd 11:0:0:0: [sdi] Attached SCSI disk
Nov  3 16:39:12 Gandalf ata_id[4999]: HDIO_GET_IDENTITY failed for '/dev/sdi': Invalid argument
Nov  3 16:39:19 Gandalf kernel: [ 7612.912125] usb 3-1: reset high-speed USB device number 3 using ehci_hcd
```

I saw that the same problem has been reported also here: [https://bbs.archlinux.org/viewtopic.php?id=152011]("https://bbs.archlinux.org/viewtopic.php?id=152011")

Any idea on how to solve it?

Bye

---


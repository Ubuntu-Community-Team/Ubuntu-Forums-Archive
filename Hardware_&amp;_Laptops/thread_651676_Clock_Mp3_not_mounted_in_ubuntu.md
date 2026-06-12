---
title: "Clock Mp3 not mounted in ubuntu"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by deusr on 2007-12-27
Folks, my father uses ubuntu (7.10) on the machine and I gave him a clock for MP3, FM and writer of this. The problem is that the ubuntu not mount it, but recognize.

Obs.: The MAC of my sister set a good and my gentoo.

Command **lsusb **
```
Bus 001 Device 002: ID 066f:8000 SigmaTel, Inc.
```
*It was found that the plug-in the device, it is recognized. *

Command **dmesg | tail**
```
[  283.036187] scsi 3:0:0:0: Direct-Access     SigmaTel MSCN             0100 PQ: 0 ANSI: 4
[  283.047136] sd 3:0:0:0: [sdb] 488576 2048-byte hardware sectors (1001 MB)
[  283.054124] sd 3:0:0:0: [sdb] Write Protect is off
[  283.054129] sd 3:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[  283.054133] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  283.073097] sd 3:0:0:0: [sdb] 488576 2048-byte hardware sectors (1001 MB)
[  283.080089] sd 3:0:0:0: [sdb] Write Protect is off
[  283.080094] sd 3:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[  283.080097] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  283.080103]  sdb:<6>usb 1-3: reset full speed USB device using ohci_hcd and address 3
```
*Note that the device tries to be assembled and dismantled shortly after.*

Command **cat / proc / partitions**
```
8 16 977152 sdb
```
*Note that the device is recognized in the machine.*

Command **ls-l / dev / sd ***
```
brw-rw---- 1 root disk 8, 0 2007-12-27 14:40 /dev/sda
brw-rw---- 1 root disk 8, 1 2007-12-27 14:40 /dev/sda1
brw-rw---- 1 root disk 8, 2 2007-12-27 16:40 /dev/sda2
brw-rw---- 1 root disk 8, 3 2007-12-27 16:40 /dev/sda3
brw-rw---- 1 root disk 8, 4 2007-12-27 14:40 /dev/sda4
```

---

### Post by taurus on 2007-12-27
What's the output of 

```
sudo fdisk -l
```

---

### Post by deusr on 2007-12-27
The device does not appear

```
jmaria@anubis:~$ sudo fdisk -l
[sudo] password for jmaria:

Disco /dev/sda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01270127

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1         255     2048256    7  HPFS ou NTFS
/dev/sda2             256         863     4883760   83  Linux
/dev/sda3             864        1183     2570400   83  Linux
/dev/sda4            1184        1245      498015   82  Linux swap / Solaris

```

---


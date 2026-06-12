---
title: "ipod mini will not mount"
date: 2009-07-06
forum: Hardware
---

### Post by SteveNorman on 2009-07-06
Im trying to use an ipod mini (1st gen I believe) to mount. I would like to be able to just mount and then copy from my ~/music into it.  I keep error messages about wrong file type, so here goes:

ubuntu 9.04
fluxbox

gnome does auto detect it, but the results are inconsistent in gnome for me, and I cant put rockbox on it with out a mount point that works.

lsusb:
```
:~$ lsusb
Bus 001 Device 014: ID 05ac:1205 Apple, Inc. iPod Mini 1.Gen/2.Gen
Bus 001 Device 013: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 004: ID 03f0:5c11 Hewlett-Packard Photosmart C4200 Printer series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:003c Microsoft Corp. SideWinder Joystick
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
steve@teampeanut:~$ 

```

fstab:
```

/dev/sdd2 /home/steve/ipod vfat users,exec,noauto,managed 0 0
```

varlog when plugging the little ******* in to usb:
```
Jul  6 15:23:06 teampeanut kernel: [ 5531.376338] usb 1-1.2: new high speed USB device using ehci_hcd and address 15
Jul  6 15:23:06 teampeanut kernel: [ 5531.470228] usb 1-1.2: configuration #1 chosen from 1 choice
Jul  6 15:23:06 teampeanut kernel: [ 5531.470783] scsi12 : SCSI emulation for USB Mass Storage devices
Jul  6 15:23:11 teampeanut kernel: [ 5536.468998] scsi 12:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Jul  6 15:23:11 teampeanut kernel: [ 5536.486588] sd 12:0:0:0: [sdd] 7999487 512-byte hardware sectors: (4.09 GB/3.81 GiB)
Jul  6 15:23:11 teampeanut kernel: [ 5536.487581] sd 12:0:0:0: [sdd] Write Protect is off
Jul  6 15:23:11 teampeanut kernel: [ 5536.489834] sd 12:0:0:0: [sdd] 7999487 512-byte hardware sectors: (4.09 GB/3.81 GiB)
Jul  6 15:23:11 teampeanut kernel: [ 5536.490826] sd 12:0:0:0: [sdd] Write Protect is off
Jul  6 15:23:11 teampeanut kernel: [ 5536.490843]  sdd: sdd1 sdd2
Jul  6 15:23:11 teampeanut kernel: [ 5536.759724] sd 12:0:0:0: [sdd] Attached SCSI removable disk
Jul  6 15:23:11 teampeanut kernel: [ 5536.759870] sd 12:0:0:0: Attached scsi generic sg5 type 0

```

results of mount attempt:
```
$ mount ipod
mount: wrong fs type, bad option, bad superblock on /dev/sdd2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

gparted recognises it as /dev/sdd2 and fat32. Im at a loss,

---

### Post by SteveNorman on 2009-07-07
got sansa clips from newegg OTW, but it would be nice to know wats wrong.

---


---
title: "can see windows partion in file manager"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by burnhamd on 2005-05-19
I  partioned my disk on installation on an 80GB sata drive with windows XP x64 having 26gb and ubuntu having 14gb
when i run fdisk it says
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   c  W95 FAT32 (LBA)
dev/sda2            3265        5209    15623212+  83  Linux
 then i  goto dev/a/sda1 and it says it can be found.
in kde when i click on media under koqueror it has both listed but only sda2 is mounted and i cant mount the other.

---

### Post by nad on 2005-05-19
It seems that nautilus is confused.

What is the ouptut of the terminal command: dmesg | grep -1i sda

---

### Post by burnhamd on 2005-05-19
this is the output
Kernel command line: root=/dev/sda2 ro console=tty0 quiet splash
Initializing CPU#0
--
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host2/bus0/target0/lun0: p1 p2
Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
EXT3 FS on sda2, internal journal
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2

---

### Post by nad on 2005-05-20
Please see this post for a possible answer:

[http://www.ubuntuforums.org/showthread.php?t=31708&highlight=sata+ahci](http://www.ubuntuforums.org/showthread.php?t=31708&highlight=sata+ahci)

---


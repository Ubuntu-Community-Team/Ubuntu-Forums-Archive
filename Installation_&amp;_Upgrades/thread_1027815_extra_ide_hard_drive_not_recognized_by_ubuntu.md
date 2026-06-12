---
title: "extra ide hard drive not recognized by ubuntu"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by chipw on 2009-01-01
Just installed a formerly windoze hd (WD800) in my ubuntu 8.1 box. The BIOS recognized the drive fine, but Ubuntu doesn't. I believe it should come up as hda or something similar. When I 'dmesg | grep hd' all I get is this -
chip@ubuntu:~$ dmesg | grep hd

[   45.825639] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX

Then I see this, which, correct me if I'm wrong, is related to the add-on drive -

[   34.167241] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   34.183883] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   34.518275] ata4.01: ATA-6: WDC WD800JB-00ETA0, 77.07W77, max UDMA/100
[   34.534567] ata4.01: 156301488 sectors, multi 16: LBA48 
[   34.566130] ata4.01: configured for UDMA/100
[   34.598962] ata_piix 0000:00:1f.2: MAP [ P1 -- P0 -- ]

I also noticed there are no hd* devices in /dev. I don't know if that has anything to do with it.

Any suggestions on how to get this drive recognized so I can see whats on it?
--
Thanks
Chip

---

### Post by taurus on 2009-01-01
It could be /dev/sdb instead of /dev/hdb.

Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by chipw on 2009-01-01
I already have 2 sata hard drives, the drive I added is the first IDE drive.

```

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196032   83  Linux

```

```

chip@ubuntu:~$ sudo blkid
/dev/sdb1: UUID="e346a514-fbed-4464-a5bd-fb596e0b2257" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="66895932-45c7-4b13-bb44-d81a4817121d" 
/dev/sdc1: UUID="e24a4b0b-2730-4336-8380-7994476e25ff" SEC_TYPE="ext2" TYPE="ext3" 

```

```

chip@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e346a514-fbed-4464-a5bd-fb596e0b2257 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=66895932-45c7-4b13-bb44-d81a4817121d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs auto,devmode=0666 0 0
# /dev/sdb1
/dev/sdb1     /drive2     ext3     defaults     1

```

```

chip@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             226G  184G   31G  86% /
varrun               1014M  256K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   56K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1             226G  184G   31G  86% /drive2
gvfs-fuse-daemon      226G  184G   31G  86% /home/chip/.gvfs

```

---

### Post by chipw on 2009-01-02
Any more ideas?

---

### Post by chipw on 2009-01-03
Any suggestions?

---

### Post by chipw on 2009-01-04
bump

---

### Post by chipw on 2009-01-07
Bump again. Anybody - help?

---

### Post by chipw on 2009-01-14
Bump

---


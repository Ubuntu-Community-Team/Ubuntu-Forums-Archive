---
title: "Cannot mount hde, please help"
date: 2005-05-13
forum: Hardware &amp; Laptops
---

### Post by registerera on 2005-05-13
I cannot mount the C:\ windows partition on boot, I have sdb2 which is ntfs working on boot. I cannot get /dev/hde5 to mount on boot either, but they both mount when I'm in ubuntu.

Can someone tell me how I set fstab up or what I need to do to mount /dev/hde1 and /dev/hde5 on boot? And from my understanding setting fmask=777,dmask=777 allows R/W on NTFS partitions. what does 222 and 333 do?


hde partition

```
Disk geometry for /dev/hde: 0.000-38166.679 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031   3522.062  primary   ntfs        boot
2       3522.063  38162.219  extended              lba
5       3522.094  38162.219  logical   ntfs
Information: Don't forget to update /etc/fstab, if necessary.
```

/etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde5       /home/jim/BOHR_G          ntfs ro,dmask=0222,fmask=0333 0 0
/dev/sdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/sdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb2       /home/jim/J    ntfs ro,dmask=0222,fmask=0333 0 0
/dev/hde1       /home/jim/C   ntfs ro,dmask=0222,fmask=0333 0 0

//192.168.0.2/Workspace%20(H) /home/jim/Workspace_H smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0  0
//192.168.0.2/Temp%20(E) /home/jim/Temp_E smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0  0
//192.168.0.2/Workspace (H) /home/jim/Workspace_H smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0  0
```

---

### Post by registerera on 2005-05-14
This Stinks! I've tried everything to setup samba to windows network and mount ntfs drives, and no one here can help me?? Booooo

---

### Post by alastair on 2005-05-14
There's no point moaning about it. It's not our job to help you. You didn't even wait 24 hours before griping!

Firstly - note that NTFS is read-only - write support is probably not enabled because it is not safe.

I would check you system logs and see what happens at boot - probe and recognition of :

IDE devices
disk/partitions

Look in : /var/log/syslog

Anything?

e.g. I see things like :

```

Probing IDE interface ide0...
hda: ST9100823A, ATA DISK drive
...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
...
EXT3 FS on hda3, internal journal
EXT3-fs: mounted filesystem with ordered data mode.

```

Then, perhaps try a different mount point (sda6 will have to be mounted BEFORE hde5 in your current config) e.g. mount under /mnt (say), as a test.

---


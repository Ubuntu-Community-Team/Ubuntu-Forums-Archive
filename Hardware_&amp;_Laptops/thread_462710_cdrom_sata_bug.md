---
title: "cdrom sata bug?"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by grimmson on 2007-06-03
Hello again. repeatable dvd-rom problem here. after two clean installs /dev/scd0 still has a problem. Cd's seem fine but dvd's don't play. any attempt to play a movie results in a slowdown / freeze and a popup window advises me to unmount drive or problems could result (don't remember exact words.) When trying to play a dvd it seems to attempt to read off the hard drive, not the sata cdrom (according to the lights.) dmesg clearly displays a problem I cannot interpret so hopefully you can.
```
   39.398945] EXT3 FS on hda4, internal journal
  39.398952] EXT3-fs: mounted filesystem with ordered data mode.
   39.425157] kjournald starting.  Commit interval 5 seconds
   39.425431] EXT3 FS on sda1, internal journal
   39.425439] EXT3-fs: mounted filesystem with ordered data mode.
   40.058240] Using specific hotkey driver
   40.195585] input: Power Button (FF) as /class/input/input5
   40.201579] ACPI: Power Button (FF) [PWRF]
   40.254225] input: Power Button (CM) as /class/input/input6
   40.254530] ACPI: Power Button (CM) [PWRB]
   40.398472] No dock devices found.
   40.423106] ibm_acpi: ec object not found
   40.507621] pcc_acpi: loading...
   40.798540] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors version 2.00.00)
   40.798614] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
   40.798619] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
   40.798624] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
   40.798629] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
   40.798633] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
   40.798637] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
   22.520000] Time: acpi_pm clocksource has been installed.
   23.928000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
   25.124000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
   25.124000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   25.124000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
   26.016000] ppdev: user-space parallel port driver
   26.608000] NET: Registered protocol family 17
   26.660000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
   26.660000] apm: overridden by ACPI.
   26.788000] Bluetooth: Core ver 2.11
   26.788000] NET: Registered protocol family 31
   26.788000] Bluetooth: HCI device and connection manager initialized
   26.788000] Bluetooth: HCI socket layer initialized
   26.804000] Bluetooth: L2CAP ver 2.8
   26.804000] Bluetooth: L2CAP socket layer initialized
   26.928000] Bluetooth: RFCOMM socket layer initialized
   26.928000] Bluetooth: RFCOMM TTY layer initialized
   26.928000] Bluetooth: RFCOMM ver 1.8
   29.548000] NET: Registered protocol family 10
   29.548000] lo: Disabled Privacy Extensions
   40.264000] eth0: no IPv6 routers present
   62.988000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
   62.988000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0xa3 data 16 ut
   62.988000]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)[   69.992000] ata2: port is slow to respond, please be patient (Status 0xc0)
   93.008000] ata2: port failed to respond (30 secs, Status 0xc0)
   93.008000] ata2: soft resetting port
   93.164000] ATA: abnormal status 0x7F on port 0x0001b807
   93.180000] ATA: abnormal status 0x7F on port 0x0001b807
   93.344000] ATA: abnormal status 0xC0 on port 0x0001b807
   93.344000] ATA: abnormal status 0xC0 on port 0x0001b807
   93.344000] ATA: abnormal status 0xC0 on port 0x0001b807
   93.344000] ATA: abnormal status 0xC0 on port 0x0001b807
   93.344000] ATA: abnormal status 0xC0 on port 0x0001b807
  123.348000] ata2.00: qc timeout (cmd 0xa1)
  123.348000] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
  123.348000] ata2.00: revalidation failed (errno=-5)
  123.348000] ata2: failed to recover some devices, retrying in 5 secs
  135.356000] ata2: port is slow to respond, please be patient (Status 0xc0)
  158.372000] ata2: port failed to respond (30 secs, Status 0xc0)
  158.372000] ata2: soft resetting port
  158.528000] ATA: abnormal status 0x7F on port 0x0001b807
  158.540000] ATA: abnormal status 0x7F on port 0x0001b807
  158.708000] ATA: abnormal status 0xC0 on port 0x0001b807
  158.708000] ATA: abnormal status 0xC0 on port 0x0001b807
  158.708000] ATA: abnormal status 0xC0 on port 0x0001b807
  158.708000] ATA: abnormal status 0xC0 on port 0x0001b807
  158.708000] ATA: abnormal status 0xC0 on port 0x0001b807
  188.720000] ata2.00: qc timeout (cmd 0xa1)
  188.720000] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
  188.720000] ata2.00: revalidation failed (errno=-5)
  188.720000] ata2.00: limiting speed to UDMA/100:PIO3
  188.720000] ata2: failed to recover some devices, retrying in 5 secs
  200.728000] ata2: port is slow to respond, please be patient (Status 0xc0)
  223.744000] ata2: port failed to respond (30 secs, Status 0xc0)
  223.744000] ata2: soft resetting port
  223.900000] ATA: abnormal status 0x7F on port 0x0001b807
  223.916000] ATA: abnormal status 0x7F on port 0x0001b807
  224.084000] ATA: abnormal status 0xC0 on port 0x0001b807
  224.084000] ATA: abnormal status 0xC0 on port 0x0001b807
  224.084000] ATA: abnormal status 0xC0 on port 0x0001b807
  224.084000] ATA: abnormal status 0xC0 on port 0x0001b807
  224.084000] ATA: abnormal status 0xC0 on port 0x0001b807
  254.088000] ata2.00: qc timeout (cmd 0xa1)
  254.088000] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
  254.088000] ata2.00: revalidation failed (errno=-5)
  254.088000] ata2.00: disabled
  254.592000] ata2: EH complete
  254.596000] VFS: busy inodes on changed media.
  254.600000] VFS: busy inodes on changed media.
  254.784000] VFS: busy inodes on changed media.
  254.784000] VFS: busy inodes on changed media.
  254.788000] VFS: busy inodes on changed media.
  655.152000] VFS: busy inodes on changed media.
  655.156000] VFS: busy inodes on changed media.
  693.700000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
grimmson@ubuntu3200:~$ \

```

 cat /etc/fstab
```
{grimmson@ubuntu3200:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=64ec2b06-579e-4f2a-bc9a-52605bf29184 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=dccecb68-4d38-4af7-b34d-b64fbba1ff9c /home           ext3    defaults        0       2
# /dev/hda1
UUID=86084DDA084DCA3F /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=d3bc0ab5-62a3-478f-b102-508ccd781e99 /media/hda2     ext3    defaults        0       2
# /dev/hda4
UUID=b2034fbf-0427-4261-b84c-a147a809f90d /media/hda4     ext3    defaults        0       2
# /dev/sda1
UUID=0d8960bd-c1e2-4af6-b120-c847e0995006 /media/sda1     ext3    defaults        0       2
# /dev/sda5
UUID=8c1d28ea-c35b-4791-a5dc-1da221ee7aea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
grimmson@ubuntu3200:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=64ec2b06-579e-4f2a-bc9a-52605bf29184 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=dccecb68-4d38-4af7-b34d-b64fbba1ff9c /home           ext3    defaults        0       2
# /dev/hda1
UUID=86084DDA084DCA3F /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=d3bc0ab5-62a3-478f-b102-508ccd781e99 /media/hda2     ext3    defaults        0       2
# /dev/hda4
UUID=b2034fbf-0427-4261-b84c-a147a809f90d /media/hda4     ext3    defaults        0       2
# /dev/sda1
UUID=0d8960bd-c1e2-4af6-b120-c847e0995006 /media/sda1     ext3    defaults        0       2
# /dev/sda5
UUID=8c1d28ea-c35b-4791-a5dc-1da221ee7aea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
grimmson@ubuntu3200:~$ 
}

```
grimmson@ubuntu3200:~$ uname -r
2.6.20-16-generic
with all fiesty updates. 

btw the drive is a  LG (life's good "ha ha ha") GSA-=H62L
 Any tips are appriciated or is this a bug?

p.s. its been so long I don't remember how to

---


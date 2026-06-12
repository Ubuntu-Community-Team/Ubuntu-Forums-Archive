---
title: "lost cdrom devices"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by equilibrium on 2005-05-08
I've just done a new install of hoary 5.04.

I did a new install yesterday on a clean SATA HDD. But now I have added my old IDE HDD I seem to have lost my cdrom devices "/dev/scd*" :( and it doesn't seem to pickup my IDE drive

I tried a few commands to lookup the problem etc :(.

```
dmesg | grep cdrom
```
```
# dmesg | grep scsi
scsi0 : ata_piix
scsi1 : ata_piix
Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
scsi2 : SCSI emulation for USB Mass Storage devices
scsi3 : SCSI emulation for USB Mass Storage devices
Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
Attached scsi generic sg1 at scsi2, channel 0, id 0, lun 0,  type 0
 /dev/scsi/host3/bus0/target0/lun0: p1
Attached scsi removable disk sdc at scsi3, channel 0, id 0, lun 0
Attached scsi generic sg2 at scsi3, channel 0, id 0, lun 0,  type 0

```
```
# lsmod | grep cdrom
cdrom                  36508  1 sr_mod
```
```
# lsmod | grep ide
video                  16260  0
ide_core              118988  2 piix,usb_storage

```
```
# dmesg | grep ide
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

```

I tried loading the ide-scsi module but it doesn't seem to make any difference :( and as dmesg gives me nothing on cdrom I'm a bit stuck :(

arg  ](*,)

---

### Post by equilibrium on 2005-05-08
ah soz :)

I got ide working now by adding this to /etc/modules
```
# ide
ide-cd
ide-disk
ide-generic
ide-core
ide-scsi

```

now just need to edit fstab to add the ide drives and mount points  :)

---


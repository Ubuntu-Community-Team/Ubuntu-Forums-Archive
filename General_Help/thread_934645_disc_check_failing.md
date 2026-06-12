---
title: "disc check failing"
date: 2008-09-30
forum: General Help
---

### Post by yon2501 on 2008-09-30
for some reason my automatic disc check keeps failing every time i let it run. it gets to about 5% then crashes and tells me i have to to a manual fsck, i tried that but then that fails. i can boot by skipping the check but id like to resolve this.

---

### Post by gombadi on 2008-09-30
Can you post the output you get when you manually run fsck so we can see what errors it is giving?

---

### Post by Dr Small on 2008-09-30
It could be hard drive failure, unless you are absolutely certain it couldn't be. I had a bad drive that did the identical same thing, and lost a bunch of files after I manually ran fsck.

---

### Post by yon2501 on 2008-10-01
this is all it says
```
fsck.ext3: Unable to resolve 'UUID=af08b12f-fbaf-4238-a004-52ac5f7aa75d'
```
and im fairly certain its not the hd, its running dual boot win/buntu and windows runs just fine

---

### Post by gombadi on 2008-10-01
It looks like it is having trouble matching the UUID with an actual disk.

Can you show the output of the following -

```

cat /etc/fstab
ls -l /dev/disk/*

```

---

### Post by yon2501 on 2008-10-01
ok heres what i got
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=af08b12f-fbaf-4238-a004-52ac5f7aa75d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b5018b69-4ac0-4ff9-bd05-9515973d029e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/disk/by-id:
total 0
lrwxrwxrwx 1 root root  9 2008-10-01 16:53 ata-Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL -> ../../sda
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 ata-Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 ata-Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 ata-Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 ata-Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 2008-10-01 16:53 scsi-1ATA_Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL -> ../../sda
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 scsi-1ATA_Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 scsi-1ATA_Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 scsi-1ATA_Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 scsi-1ATA_Hitachi_HTS721010G9SA00_MPCZN7Y0GZG2UL-part6 -> ../../sda6

/dev/disk/by-path:
total 0
lrwxrwxrwx 1 root root  9 2008-10-01 16:53 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 pci-0000:00:1f.2-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 pci-0000:00:1f.2-scsi-0:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 pci-0000:00:1f.2-scsi-0:0:0:0-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 pci-0000:00:1f.2-scsi-1:0:0:0 -> ../../scd0

/dev/disk/by-uuid:
total 0
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 3EB83A5CB83A12BF -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 af08b12f-fbaf-4238-a004-52ac5f7aa75d -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-10-01 16:53 b5018b69-4ac0-4ff9-bd05-9515973d029e -> ../../sda6
```

---


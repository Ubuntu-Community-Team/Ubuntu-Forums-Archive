---
title: "CD / DVD Mounting issue"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by JediPottsy on 2007-07-11
Hi

i am unable to use cd's and DVD's once into linux. It happened in fedora aswell as ubuntu. I know the drives work as i installed linux using them and can use them on the windows drive.

this is the following dmesg output

```

jedipottsy@ubuntu:~$ dmesg | grep -i hd
[    4.333984]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[    4.333995]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[    4.753322] hda: WDC WD1600JB-00EVA0, ATA DISK drive
[    5.032923] hdb: SAMSUNG SP0802N, ATA DISK drive
[    5.975576] hdc: ATAPI-CD ROM-DRIVE-56MAX, ATAPI CD/DVD-ROM drive
[    6.758457] hdd: LITE-ON DVDRW LDW-851S, ATAPI CD/DVD-ROM drive
[    6.822041] hda: max request size: 512KiB
[    6.925437] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[    6.927222] hda: cache flushes supported
[    6.927256]  hda: hda1
[    6.951562] hdb: max request size: 512KiB
[    6.951641] hdb: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[    6.951849] hdb: cache flushes supported
[    6.951868]  hdb:<6>usb 1-2: configuration #1 chosen from 1 choice
[    6.971912]  hdb1 hdb2 <<6>input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input1
[    6.993418]  hdb5 >
[    6.995445] hdc: ATAPI 56X CD-ROM drive, 128kB Cache, UDMA(33)
[    6.998556] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   17.104453] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   17.105946] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   21.019076] EXT3 FS on hdb1, internal journal

```

and this is my fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a5380e00-f7df-4543-a42d-d1741d76ba76 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=1c20cdad-2469-49a9-9bdd-6f5f7533a9ae none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660     0       0
/dev/hdc        /media/cdrom1   udf,iso9660     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

no drives appear under computer

```

jedipottsy@ubuntu:~$ ls -l /dev/hd*
brw-rw---- 1 root disk   3,  0 2007-07-11 22:56 /dev/hda
brw-rw---- 1 root disk   3,  1 2007-07-11 22:56 /dev/hda1
brw-rw---- 1 root disk   3, 64 2007-07-11 22:56 /dev/hdb
brw-rw---- 1 root disk   3, 65 2007-07-11 21:56 /dev/hdb1
brw-rw---- 1 root disk   3, 66 2007-07-11 22:56 /dev/hdb2
brw-rw---- 1 root disk   3, 69 2007-07-11 22:56 /dev/hdb5
brw-rw---- 1 root cdrom 22,  0 2007-07-11 22:56 /dev/hdc
brw-rw---- 1 root cdrom 22, 64 2007-07-11 22:56 /dev/hdd

```

```

jedipottsy@ubuntu:/dev$ sudo mount /dev/hdd /media/cdrom0
mount: No medium found

```

argh!

---

### Post by EXCiD3 on 2007-07-12
It almost looks like it views your cdrom drive as a hdd...

---


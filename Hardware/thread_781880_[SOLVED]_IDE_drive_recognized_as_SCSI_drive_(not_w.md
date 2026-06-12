---
title: "[SOLVED] IDE drive recognized as SCSI drive (not working) by Hardy"
date: 2008-05-04
forum: Hardware
---

### Post by slayer^_^ on 2008-05-04
Neither Hardy Live CD or hardy Heron fresh-installed let me work with the two partitions I got on my IDE drive. Notably on that IDE hard drive there is a windows partition (that was, obviously, removed from GRUB, and I had to add it manually) and an archive ext3 partition. My Ubuntu partition, the swap one and another ext3 archive partition are on the primary SATA drive.

Please note that :

1) If i boot with the option "all_generic_ide" the partitions are visible, but the general performance is compromised and I experience system lock-ups.

2) Everything worked ok with Gutsy

3) During the installation of Hardy the install program recognizes the partitions.

4) In nautilus i can't even see the two partitions on the IDE drive, but just a SCSI drive that ubuntu is unable to mount.


here's the output of "sudo fdisk -l"

Disco /dev/sda: 122.9 GB, 122942324736 byte
255 heads, 63 sectors/track, 14946 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90399039

Dispositivo Boot Start End Blocks Id System
/dev/sda1 * 1 1804 14490598+ 7 HPFS/NTFS
/dev/sda2 1805 14946 105563115 f W95 Esteso (LBA)
/dev/sda5 1805 14946 105563083+ 83 Linux

Disco /dev/sdb: 250.0 GB, 250059350016 byte
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd624f0be

Dispositivo Boot Start End Blocks Id System
/dev/sdb1 * 1 2791 22418612 83 Linux
/dev/sdb2 2792 3041 2008092 82 Linux swap / Solaris
/dev/sdb3 3042 30401 219769168 83 Linux

sda is the IDE drive, sdb the SATA one

output of "lsb_release -rd"

Description: Ubuntu 8.04
Release: 8.04

i attached the output of "sudo lshw".

**_SOLUTION_**

the solution is here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639)

Well, today we discovered on launchpad the final solution:

the ide cable!

the new modules absolutely require a 80-wire ide cable (the one with coloured pins), everyone of us who experienced this bug had 40-wire ide-cables...

...and of course a good cable plugging (blue plug on motherboard, gray on slave and black on master) and a correct setting of the jumpers of the hard disks (disk set as master if it is connected to the black plug of the cable, ecc ecc).

A manually setting of the dma speed and pio mode in the motherboard bios is also a good idea.

Best regards.

---


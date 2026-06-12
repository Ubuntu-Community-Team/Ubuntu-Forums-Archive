---
title: "xubuntu hard disk problem"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by blitz_mohit on 2008-01-15
now i have a xubuntu 6.06 and i want to attach a hard disk to it..i don know anythin bout the size ..whether it is workin or not.. or has a windows installed..wat should i do ..????
tried to make my xubuntu hard disk as primary and other as slave but when i do this the hard disk which i've made as slave comes as master and the xubuntu one doesnt show in the bios setup..also tried to run from a xubuntu live cd but that gives a previous error which was solved by addin pci=routeirq which was suggested in the installation category..tried that also but live cd wont work too..

link to last problem with live cd
[http://ubuntuforums.org/showthread.php?t=665392](http://ubuntuforums.org/showthread.php?t=665392)

config::
pentium 3<451mhz>
256 ram(2*128 chip)
40 Gb Hdd
52x cd writer
i440BX motherboard
nvidia 8 Mb graphics card

---

### Post by logos34 on 2008-01-15
did you check the jumper on the slave drive?

---

### Post by blitz_mohit on 2008-01-15
don know wat dat this..???

---

### Post by logos34 on 2008-01-15
little plastic thingy on the back of the drive.  IDE drives have to be set for either master or slave to correspond to their position of the ribbon cable (or set both to 'cable select')

---

### Post by blitz_mohit on 2008-01-15
its on the first one<left hand side> wat should i do with it put on the second or third..???

---

### Post by logos34 on 2008-01-15
every drive is different--if there's no sticker with a diagram then check the manual (->manufacturer website)

---

### Post by blitz_mohit on 2008-01-17
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4772 38331058+ 83 Linux
/dev/hda2 4773 4865 747022+ 5 Extended
/dev/hda5 4773 4865 746991 82 Linux swap / Solaris

Disk /dev/hdb: 8447 MB, 8447459328 bytes
240 heads, 63 sectors/track, 1091 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 1091 8247928+ c W95 FAT32 (LBA)

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 126 1007584 b W95 FAT32
Partition 1 has different physical/logical endings:
phys=(124, 254, 63) logical=(125, 112, 50)

---

### Post by logos34 on 2008-01-17
it's showing up now as primary slave.  

Add it to fstab so it automounts at boot:
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-58b0f4b165129f43a80bba6c1c4227c490efa119](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-58b0f4b165129f43a80bba6c1c4227c490efa119)

---

### Post by blitz_mohit on 2008-01-18
i think this drive has bad sectors..is there any utility that helps me get rid of them..??

---


---
title: "only 1st partition automounted on external usb disk"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by jure1873 on 2007-02-25
I've got an external usb disk and when I plug it in kde automatically mounts and displays only the first partition on that disk. Sometimes it displays all of them, usually I get all of them if I start the pc with the disk plugged in. I can manually mount those partitions, but I don't know why it doesn't do it automatically. If I go to storage media with konqueror I also see only the sda1 partition.

# fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 glav, 63 sektorjev/stezo, 30401 stez
Enote = cylinders od 16065 x 512 = 8225280 bajtov

  Naprava Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15201   122102001   83  Linux
/dev/sda2           15202       28255   104856255    b  W95 FAT32
/dev/sda3           28256       30401    17237745   83  Linux

---


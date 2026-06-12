---
title: "Issue with external Hardrive"
date: 2020-09-29
forum: Hardware
---

### Post by juraj-papic on 2020-09-29
Hi all,

I have my external usb 4Tb and is not mounting If I do a "fdisk -l" i will only see "partition gpt in /dev/sda"  Then I did "fsck -fyc /dev/sda"  and I got this output e2fsck -b 8193 <dispositivo>  or  e2fsck -b 32768 <dispositivo> I need to recover my data.


Thanks in advance.

---

### Post by TheFu on 2020-09-29
/dev/sda is the whole drive, not any partition.  Partitions need file systems.  /dev/sda1 would be the first partition on drive sda.  Running commands meant for partitions on the whole drive can break things.

Please show commands AND outputs.

---

### Post by juraj-papic on 2020-09-29
This will be the output 

Dispositivo Comienzo      Final   Sectores Tamaño Tipo
/dev/sda1       2048 7813967871 7813965824   3,7T Datos básicos de Microsoft

This is what I get ,, I try to see it with gparted but its always "searching /dev/sda partition"

thanks.

---

### Post by TheFu on 2020-09-29
sda1 isn't a linux file system.  any data recovery will need to be performed using ms-windows.

If the file system was last mounted by windows, then it is likely that windows did not close the file system. This has been common since win8 was released. You'll need to use windows to properly close the file system. Linux cannot do this.  Thre are how-to guides on windows forums for that task.

---

### Post by juraj-papic on 2020-09-29
thanks!!

---


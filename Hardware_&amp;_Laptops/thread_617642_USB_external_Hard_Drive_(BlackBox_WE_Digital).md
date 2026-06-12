---
title: "USB external Hard Drive (BlackBox WE Digital)"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by Mister Mamat on 2007-11-19
Hi folks,

I've got an external hard drive : BlackBox WE digital.

Notebook HP ZD7000
Ubuntu Gutsy 7.10
kernel 2.6.22-14-generic

2 external hard disk USB
-80 Go Western Digital (no worries, auto mount...)
-500 Go BlackBox WE digita (this problem).

```
lsusb
Bus 004 Device 034: ID 067b:2507 Prolific Technology, Inc. PL2507 Hi-speed USB to IDE bridge controller
```

BlackBox seems to be "physically" recognized by my system (...)

but no auto mount and nothing in the /dev

```
ls -l /dev/disk/by-id
total 0
lrwxrwxrwx 1 root root  9 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T -> ../../sda
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T -> ../../sda
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part6 -> ../../sda6
```

toshiba is my internal hard disk.

I unplug my blackbox to test the WD one (together nothing work)

auto mount = OK and

```
lsusb
Bus 004 Device 035: ID 1058:0701 Western Digital Technologies, Inc.

```

and

```

ls -l /dev/disk/by-id
total 0
lrwxrwxrwx 1 root root  9 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T -> ../../sda
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 ata-TOSHIBA_MK6025GAS_X4MP9866T-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T -> ../../sda
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-11-15 22:15 scsi-1ATA_TOSHIBA_MK6025GAS_X4MP9866T-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 2007-11-15 23:19 usb-WDC_WD80_0VE-07HDT0_DEF10B17F205-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2007-11-15 23:19 usb-WDC_WD80_0VE-07HDT0_DEF10B17F205-0:0-part1 -> ../../sdb1

```

This kind of exernal hard disk works with ubuntu (someone told me)
And i've no problem with windows with my professional computer.

Is there anyone who have any ideas?

---

### Post by gdzsi on 2007-11-21
is it formatted?

---

### Post by gdzsi on 2007-11-21
...and not ntfs :)

---

### Post by hardin0341 on 2007-11-21
I have a USB external hard drive (formatted ntsb). It is mounted and recognized, but remains "read only" status. I have tried to change the permissions ```
Chmod 777 [file]
```, but no change.

I have files on it placed by a windows machine. I can see those file name with ```
ls -la
```, but still I can't do anything else. 

Do I have to reformat the drive to use it with my Ubuntu Server 6.06? I also want to access via Samba Sever - here I can see it from the Client's workstations, but cannot access anything on the drive.

Thank so much for all you all do! Any clues would be helpful!

---

### Post by FRuMMaGe on 2007-11-21
Linux cannot write natively to NTFS drives without extra software.

Format it to FAT32 if you want to share it with Windows, or Ext3 for Linux only.

---

### Post by hardin0341 on 2007-11-21
Thank you for the information. I'll transfer the files back to a Windows machine, then format to FAT32. I'm not sure how to do that as I'm a newbie, but I'll Google my heart out and find out how! Thanks for the information once again!

---

### Post by Mister Mamat on 2007-11-22
GDZSY, yes it's formatted in ntfs. But the real trouble is i really cannot get any access to it.

Sometimes, ubuntu's trying to access it but it say : "it's imposible to mount use windows and dismount it correctly or try to force it with something like :
sudo mount -t ntfs-3g /dev/sdb1 /media/BlackBox -o force.
it's working for a couple of second and it desappear...

All the time, i just can see it with lsusb command. And when i try to force it to mount, it told me that sdb1 doesn't exist.

Newt try, i'll bring my Hard disc to my office to try it with windows...

About ntfs writing permission, i've install ntfs-config. And it seems to be good enough to write in yours ntfs partitions.


cheers
Mat

---

### Post by hardin0341 on 2007-11-22
@Mister Mamut: GDZSY?? Sorry, clueless on that one. 

Formatted** /dev/sdb1** to** vfat** , not sure why I can't do the same for **/dev/sdb2** ....  Also, not sure why my 160 GB External HDD is being split up in to two different "mount points (?)".

Any information?? Thanks!

---


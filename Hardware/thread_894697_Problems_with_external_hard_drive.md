---
title: "Problems with external hard drive"
date: 2008-08-19
forum: Hardware
---

### Post by hydron on 2008-08-19
the problem is as following:
I'm using SAMSUNG  HM250JI 250gb laptop hdd in case as an external hard drive. And the hdd crashes occasionaly: the LED on the case indicates that it's writing/reading and it becomes unresponsive. This happens on windows too (much more often also). So I expect It could be a hardware problem and cannot be fixed. What could be fixed though is that when I replug the drive I would like it to be mounted in the same folder. For example:

I plug in the drive, the partitions are mounted info folders "/media/USB HDD" and "/media/Large Files/", the hdd crashes, I unplug it. The sistem does not detect that the drive has been removed, so when I plug it back in, the drive gets mounted into folders "/media/USB HDD_" and "/media/Large Files_". The folders "/media/USB HDD" and "/media/Large Files" remain also. SO when the drive crashes once more I have more folders on the screen with longer dashes at the end. So if a program needs to access a file on the hdd I have to change the address of the file accordingly. That is quite annoying.

Some more info. Dmesg when I plug in the drive:
> [ 5069.115028] usb 5-8: new high speed USB device using ehci_hcd and address 20
[ 5069.247813] usb 5-8: configuration #1 chosen from 1 choice
[ 5069.277599] scsi8 : SCSI emulation for USB Mass Storage devices
[ 5069.285095] usb-storage: device found at 20
[ 5069.285103] usb-storage: waiting for device to settle before scanning
[ 5074.276369] usb-storage: device scan complete
[ 5074.277247] scsi 8:0:0:0: Direct-Access     SAMSUNG  HM250JI               PQ: 0 ANSI: 2 CCS
[ 5074.291750] sd 8:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[ 5074.292426] sd 8:0:0:0: [sdc] Write Protect is off
[ 5074.292431] sd 8:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 5074.292434] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 5074.293545] sd 8:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[ 5074.294171] sd 8:0:0:0: [sdc] Write Protect is off
[ 5074.294175] sd 8:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 5074.294178] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 5074.294186]  sdc: sdc1 sdc2
[ 5074.943401] sd 8:0:0:0: [sdc] Attached SCSI disk
[ 5074.943459] sd 8:0:0:0: Attached scsi generic sg0 type 0

Partitions on the drive:
~200 GB fat32
~50 GB NTFS (on ubuntu I never used NTFS, so thats not the problem)

relevant output from "mount":
> /dev/sda2 on /media/USB HDD_ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda1 on /media/Large Files_ type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc1 on /media/Large Files__ type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc2 on /media/USB HDD__ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


I also get similar errors constantly showing up in dmesg:
> [ 5003.251792] FAT: Directory bread(block 94311) failed

To overcome the limitation of FAT32 max partition size I used some special application. Could that be a problem?

I'd appreciate your help.

---


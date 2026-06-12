---
title: "[SOLVED] USB mass storage unit automount in ubuntu-server"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by TheHilikus on 2007-11-10
I'm trying to get my ubuntu server to automount my mp3 player (MSU) as soon as it detects it. the device gets recognized, if i mount the drive manually it works. but i need it to be mounted automatically. i dont want to rely on gnome since i usually dont have it running. i tried ivman but it didnt work either, it seems it doesnt get the update event. when i run it as a normal user and in the fg it doesnt show anything when the device is plugged in

i tried lshal -monitor and it also doesnt show anything when i plug the device

lsusb shows this
Bus 003 Device 019: ID 0e21:0510 Cowon Systems, Inc.

and dmesg shows

```

[67718.202763] scsi 14:0:0:0: Direct-Access     TOSHIBA  MK3006GAL        BY10 PQ: 0 ANSI: 0 CCS
[67718.204362] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[67718.205238] sda: Write Protect is off
[67718.205242] sda: Mode Sense: 00 4a 00 00
[67718.205245] sda: assuming drive cache: write through
[67718.206109] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[67718.206985] sda: Write Protect is off
[67718.206989] sda: Mode Sense: 00 4a 00 00
[67718.206991] sda: assuming drive cache: write through
[67718.206994]  sda: sda1
[67718.212821] sd 14:0:0:0: Attached scsi disk sda
[67718.212869] sd 14:0:0:0: Attached scsi generic sg0 type 0

```

again, if i pmount the device manually it works ok

the reason i want to automount it is because i want to auto synchronize some directories. i also dont know how to run a command automatically on detect but i'll deal with that once the thing automounts at least

Thanks for any help

---

### Post by TheHilikus on 2007-11-13
i forgot to mention its ubuntu feisty server, i did install the basic gnome environment but again, i dont want to rely on it running cause sometimes it is not

---


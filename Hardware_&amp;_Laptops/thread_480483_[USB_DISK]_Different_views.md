---
title: "[USB DISK] Different views?"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by gerrold on 2007-06-21
Hi guys,
I've just bought an external  HD 80Gb (Microspot High speed SlimlDrive) and formatted with Partition Magic (on WinXP) as single partition FAT32.

I have two laptops: L1 e L2.

Now:
1) on win (L1) I can see and use the HD perfectly
2) on Ubuntu 7.04 (L1) I can see and use the HD perfectly  
(and also gparted can see it as FAT32)
3) on Ubuntu 6.10 (L2) I CANNOT see it   (and gparted can see it but says the HD is not formatted)

8-[
Tchuss.
Gerrold

p.s.
```

tail -F /var/log/messages

Jun 21 18:51:53 HP-laptop kernel: [17179849.184000] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 21 18:51:53 HP-laptop kernel: [17179849.184000] end_request: I/O error, dev sdb, sector 0
Jun 21 18:51:53 HP-laptop kernel: [17179849.188000] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 21 18:51:53 HP-laptop kernel: [17179849.188000] end_request: I/O error, dev sdb, sector 0
Jun 21 18:51:53 HP-laptop kernel: [17179849.188000] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 21 18:51:53 HP-laptop kernel: [17179849.188000] end_request: I/O error, dev sdb, sector 0
Jun 21 18:51:53 HP-laptop kernel: [17179849.192000] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 21 18:51:53 HP-laptop kernel: [17179849.192000] end_request: I/O error, dev sdb, sector 0
Jun 21 18:51:53 HP-laptop kernel: [17179849.196000] sd 5:0:0:0: SCSI error: return code = 0x10070000
Jun 21 18:51:53 HP-laptop kernel: [17179849.196000] end_request: I/O error, dev sdb, sector 0



admin@HP-laptop:~$ sudo mount /dev/sdb -t vfat /media
mount: /dev/sdb: can't read superblock


```

---


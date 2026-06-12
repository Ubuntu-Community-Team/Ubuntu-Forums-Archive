---
title: "Error repeating SATA link down"
date: 2018-05-11
forum: Hardware
---

### Post by egandt on 2018-05-11
```

May 11 09:22:01 desktop kernel: [ 1239.394720] ata4: SATA link down (SStatus 1 SControl 300)
May 11 09:22:01 desktop kernel: [ 1239.394728] ata4: EH complete
May 11 09:22:01 desktop kernel: [ 1239.404621] ata4: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
May 11 09:22:01 desktop kernel: [ 1239.404624] ata4: irq_stat 0x00000040, connection status changed
May 11 09:22:01 desktop kernel: [ 1239.404627] ata4: SError: { DevExch }
May 11 09:22:01 desktop kernel: [ 1239.404632] ata4: hard resetting link
May 11 09:22:03 desktop kernel: [ 1241.626713] ata4: SATA link down (SStatus 1 SControl 300)
May 11 09:22:03 desktop kernel: [ 1241.626720] ata4: EH complete
May 11 09:22:03 desktop kernel: [ 1241.627534] ata4: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
May 11 09:22:03 desktop kernel: [ 1241.627536] ata4: irq_stat 0x00000040, connection status changed
May 11 09:22:03 desktop kernel: [ 1241.627539] ata4: SError: { DevExch }
May 11 09:22:03 desktop kernel: [ 1241.627543] ata4: hard resetting link

```

However there is no such device:
```

root@desktop:/var/log#  lsscsi -d
[0:0:0:0]    disk    ATA      Samsung SSD 850  4B6Q  /dev/sdb [8:16]
[2:0:0:0]    cd/dvd  HL-DT-ST BD-RE  WH14NS40  1.02  /dev/sr0 [11:0]
[7:0:0:0]    disk    Adaptec  RAID6            V1.0  /dev/sda [8:0]
[7:1:0:0]    disk    ATA      ST2000VN004-2E41 SC60  -        
[7:1:1:0]    disk    ATA      ST2000VN004-2E41 SC60  -        
[7:1:2:0]    disk    ATA      ST2000VN004-2E41 SC60  -        
[7:1:3:0]    disk    ATA      ST2000VN004-2E41 SC60  -        
[7:1:4:0]    disk    ATA      ST2000VN004-2E41 SC60  -        
[7:1:5:0]    disk    ATA      ST2000VN004-2E41 SC60  -        
[7:1:6:0]    disk    ATA      ST2000VN004-2E41 SC60  -        
[7:1:7:0]    disk    ATA      ST2000VN004-2E41 SC60  -        
[10:0:0:0]   disk    Generic  STORAGE DEVICE   0310  /dev/sdc [8:32]

```

Windows has no problems so this is something Linux related (I have an idea, I have a pair of cs/dvd drives and I assume that the second that is not listed one on ata4), but I have no way to say for sure.
What I want is to disable this device on boot, but I can not find a way to do so.

Thanks,
ERIC

---

### Post by pqwoerituytrueiwoq on 2018-05-13
check the cables on the drives just to be sure, both power and data
My 1TB HDD seems to act up with every black sata cable in my case, even ones that work with other drives??? (these 4 cables came with retail motherboards)
by the random red cable from 2006 works just fine...

one time i had some strange things happen the sata cable was in at a angle (the ssd has no locking cable support)

---


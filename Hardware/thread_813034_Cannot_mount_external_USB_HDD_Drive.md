---
title: "Cannot mount external USB HDD Drive"
date: 2008-05-30
forum: Hardware
---

### Post by Lemon on 2008-05-30
Whenever i connect my external WD MyBook 320GB external USB drive, i get the following error message:

> **Cannot Mount Volume**
You are not privileged to mount the volume 'SUPERMAX'.
(message box screenshot attached)

Now, i've already read about the bug with parted leaving a lock file, and that's not the case here. Also, my dmesg looks funny.

Apart from the problem with the external drive, my DVD burner is also acting up, but that could possibly be related to it's crappiness.

Below is the weird output from dmesg, when pluggin the drive in. (The drive worked fine before installing the new ubuntu (which was done by reinstalling, not updating.))
```
[ 9863.775762] usb 4-4.4.2: new high speed USB device using ehci_hcd and address 7
[ 9863.871749] usb 4-4.4.2: configuration #1 chosen from 1 choice
[ 9863.874760] scsi5 : SCSI emulation for USB Mass Storage devices
[ 9863.876073] usb-storage: device found at 7
[ 9863.876078] usb-storage: waiting for device to settle before scanning
[ 9868.868281] usb-storage: device scan complete
[ 9868.903608] scsi 5:0:0:0: Direct-Access     WD       3200JB External  0107 PQ: 0 ANSI: 0
[ 9868.911424] sd 5:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[ 9868.912300] sd 5:0:0:0: [sdc] Write Protect is off
[ 9868.912304] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 9868.912307] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 9868.913663] sd 5:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[ 9868.914538] sd 5:0:0:0: [sdc] Write Protect is off
[ 9868.914542] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 9868.914544] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 9868.914548]  sdc: sdc1
[ 9868.920672]  sdc: p1 exceeds device capacity
[ 9868.920743] sd 5:0:0:0: [sdc] Attached SCSI disk
[ 9868.920792] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 9869.229175] attempt to access beyond end of device
[ 9869.229188] sdc: rw=0, want=625153216, limit=625142448
[ 9869.229192] Buffer I/O error on device sdc1, logical block 625153152
[ 9869.229197] attempt to access beyond end of device
[ 9869.229199] sdc: rw=0, want=625153217, limit=625142448
[ 9869.229201] Buffer I/O error on device sdc1, logical block 625153153
[ 9869.229204] attempt to access beyond end of device
[ 9869.229206] sdc: rw=0, want=625153218, limit=625142448
[ 9869.229208] Buffer I/O error on device sdc1, logical block 625153154
[ 9869.229211] attempt to access beyond end of device
[ 9869.229213] sdc: rw=0, want=625153219, limit=625142448
[ 9869.229215] Buffer I/O error on device sdc1, logical block 625153155
[ 9869.229218] attempt to access beyond end of device
[ 9869.229220] sdc: rw=0, want=625153220, limit=625142448
[ 9869.229222] Buffer I/O error on device sdc1, logical block 625153156
[ 9869.229225] attempt to access beyond end of device
[ 9869.229227] sdc: rw=0, want=625153221, limit=625142448
[ 9869.229229] Buffer I/O error on device sdc1, logical block 625153157
[ 9869.229231] attempt to access beyond end of device
[ 9869.229233] sdc: rw=0, want=625153222, limit=625142448
[ 9869.229235] Buffer I/O error on device sdc1, logical block 625153158
[ 9869.229238] attempt to access beyond end of device
[ 9869.229240] sdc: rw=0, want=625153223, limit=625142448
[ 9869.229242] Buffer I/O error on device sdc1, logical block 625153159
[ 9869.229246] attempt to access beyond end of device
[ 9869.229248] sdc: rw=0, want=625153216, limit=625142448
[ 9869.229250] Buffer I/O error on device sdc1, logical block 625153152
[ 9869.229253] attempt to access beyond end of device
[ 9869.229255] sdc: rw=0, want=625153217, limit=625142448
[ 9869.229257] Buffer I/O error on device sdc1, logical block 625153153
[ 9869.229260] attempt to access beyond end of device
[ 9869.229262] sdc: rw=0, want=625153218, limit=625142448
[ 9869.229264] attempt to access beyond end of device
[ 9869.229266] sdc: rw=0, want=625153219, limit=625142448
[ 9869.229269] attempt to access beyond end of device
[ 9869.229271] sdc: rw=0, want=625153220, limit=625142448
[ 9869.229273] attempt to access beyond end of device
[ 9869.229275] sdc: rw=0, want=625153221, limit=625142448
[ 9869.229278] attempt to access beyond end of device
[ 9869.229280] sdc: rw=0, want=625153222, limit=625142448
[ 9869.229282] attempt to access beyond end of device
[ 9869.229284] sdc: rw=0, want=625153223, limit=625142448
[ 9869.229297] attempt to access beyond end of device
[ 9869.229299] sdc: rw=0, want=625153392, limit=625142448
[ 9869.229302] attempt to access beyond end of device
[ 9869.229304] sdc: rw=0, want=625153393, limit=625142448
[ 9869.229307] attempt to access beyond end of device
[ 9869.229309] sdc: rw=0, want=625153394, limit=625142448
[ 9869.229311] attempt to access beyond end of device
[ 9869.229313] sdc: rw=0, want=625153395, limit=625142448
[ 9869.229316] attempt to access beyond end of device
[ 9869.229318] sdc: rw=0, want=625153396, limit=625142448
[ 9869.229321] attempt to access beyond end of device
[ 9869.229323] sdc: rw=0, want=625153397, limit=625142448
[ 9869.229325] attempt to access beyond end of device
[ 9869.229327] sdc: rw=0, want=625153398, limit=625142448
[ 9869.229330] attempt to access beyond end of device
[ 9869.229332] sdc: rw=0, want=625153399, limit=625142448
[ 9869.229335] attempt to access beyond end of device
[ 9869.229337] sdc: rw=0, want=625153392, limit=625142448
[ 9869.229339] attempt to access beyond end of device
[ 9869.229341] sdc: rw=0, want=625153393, limit=625142448
[ 9869.229344] attempt to access beyond end of device
[ 9869.229346] sdc: rw=0, want=625153394, limit=625142448
[ 9869.229348] attempt to access beyond end of device
[ 9869.229350] sdc: rw=0, want=625153395, limit=625142448
[ 9869.229352] attempt to access beyond end of device
[ 9869.229355] sdc: rw=0, want=625153396, limit=625142448
[ 9869.229357] attempt to access beyond end of device
[ 9869.229359] sdc: rw=0, want=625153397, limit=625142448
[ 9869.229361] attempt to access beyond end of device
[ 9869.229363] sdc: rw=0, want=625153398, limit=625142448
[ 9869.229366] attempt to access beyond end of device
[ 9869.229368] sdc: rw=0, want=625153399, limit=625142448
[ 9869.229482] attempt to access beyond end of device
[ 9869.229485] sdc: rw=0, want=625153408, limit=625142448
[ 9869.229487] attempt to access beyond end of device
[ 9869.229490] sdc: rw=0, want=625153409, limit=625142448
[ 9869.229492] attempt to access beyond end of device
[ 9869.229494] sdc: rw=0, want=625153410, limit=625142448
[ 9869.229497] attempt to access beyond end of device
[ 9869.229500] sdc: rw=0, want=625153408, limit=625142448
[ 9869.229502] attempt to access beyond end of device
[ 9869.229504] sdc: rw=0, want=625153409, limit=625142448
[ 9869.229506] attempt to access beyond end of device
[ 9869.229508] sdc: rw=0, want=625153410, limit=625142448
[ 9869.229517] attempt to access beyond end of device
[ 9869.229519] sdc: rw=0, want=625153408, limit=625142448
[ 9869.229521] attempt to access beyond end of device
[ 9869.229524] sdc: rw=0, want=625153409, limit=625142448
[ 9869.229526] attempt to access beyond end of device
[ 9869.229528] sdc: rw=0, want=625153410, limit=625142448
[ 9869.229536] attempt to access beyond end of device
[ 9869.229538] sdc: rw=0, want=625153408, limit=625142448
[ 9869.229541] attempt to access beyond end of device
[ 9869.229543] sdc: rw=0, want=625153409, limit=625142448
[ 9869.229545] attempt to access beyond end of device
[ 9869.229547] sdc: rw=0, want=625153410, limit=625142448
[ 9869.229554] attempt to access beyond end of device
[ 9869.229556] sdc: rw=0, want=625153408, limit=625142448
[ 9869.229559] attempt to access beyond end of device
[ 9869.229561] sdc: rw=0, want=625153409, limit=625142448
[ 9869.229563] attempt to access beyond end of device
[ 9869.229565] sdc: rw=0, want=625153410, limit=625142448
[ 9869.229572] attempt to access beyond end of device
[ 9869.229575] sdc: rw=0, want=625153408, limit=625142448
[ 9869.229577] attempt to access beyond end of device
[ 9869.229579] sdc: rw=0, want=625153409, limit=625142448
[ 9869.229582] attempt to access beyond end of device
[ 9869.229584] sdc: rw=0, want=625153410, limit=625142448
[ 9869.229591] attempt to access beyond end of device
[ 9869.229593] sdc: rw=0, want=625153408, limit=625142448
[ 9869.229596] attempt to access beyond end of device
[ 9869.229598] sdc: rw=0, want=625153409, limit=625142448
[ 9869.229600] attempt to access beyond end of device
[ 9869.229602] sdc: rw=0, want=625153410, limit=625142448
[ 9869.229613] attempt to access beyond end of device
[ 9869.229615] sdc: rw=0, want=625153344, limit=625142448
[ 9869.229618] attempt to access beyond end of device
[ 9869.229620] sdc: rw=0, want=625153345, limit=625142448
[ 9869.229622] attempt to access beyond end of device
[ 9869.229624] sdc: rw=0, want=625153346, limit=625142448
[ 9869.229627] attempt to access beyond end of device
[ 9869.229629] sdc: rw=0, want=625153347, limit=625142448
[ 9869.229631] attempt to access beyond end of device
[ 9869.229633] sdc: rw=0, want=625153348, limit=625142448
[ 9869.229636] attempt to access beyond end of device
[ 9869.229638] sdc: rw=0, want=625153349, limit=625142448
[ 9869.229640] attempt to access beyond end of device
[ 9869.229642] sdc: rw=0, want=625153350, limit=625142448
[ 9869.229644] attempt to access beyond end of device
[ 9869.229646] sdc: rw=0, want=625153351, limit=625142448
[ 9869.229656] attempt to access beyond end of device
[ 9869.229659] sdc: rw=0, want=625153400, limit=625142448
[ 9869.229661] attempt to access beyond end of device
[ 9869.229663] sdc: rw=0, want=625153401, limit=625142448
[ 9869.229666] attempt to access beyond end of device
[ 9869.229668] sdc: rw=0, want=625153402, limit=625142448
[ 9869.229670] attempt to access beyond end of device
[ 9869.229672] sdc: rw=0, want=625153403, limit=625142448
[ 9869.229675] attempt to access beyond end of device
[ 9869.229677] sdc: rw=0, want=625153404, limit=625142448
[ 9869.229679] attempt to access beyond end of device
[ 9869.229681] sdc: rw=0, want=625153405, limit=625142448
[ 9869.229684] attempt to access beyond end of device
[ 9869.229686] sdc: rw=0, want=625153406, limit=625142448
[ 9869.229689] attempt to access beyond end of device
[ 9869.229691] sdc: rw=0, want=625153407, limit=625142448
[ 9869.229698] attempt to access beyond end of device
[ 9869.229700] sdc: rw=0, want=625153408, limit=625142448
[ 9869.229702] attempt to access beyond end of device
[ 9869.229704] sdc: rw=0, want=625153409, limit=625142448
[ 9869.229707] attempt to access beyond end of device
[ 9869.229709] sdc: rw=0, want=625153410, limit=625142448
[ 9869.229716] attempt to access beyond end of device
[ 9869.229718] sdc: rw=0, want=625153408, limit=625142448
[ 9869.229721] attempt to access beyond end of device
[ 9869.229723] sdc: rw=0, want=625153409, limit=625142448
[ 9869.229725] attempt to access beyond end of device
[ 9869.229727] sdc: rw=0, want=625153410, limit=625142448
[ 9869.313680] attempt to access beyond end of device
[ 9869.313692] sdc: rw=0, want=625153216, limit=625142448
[ 9869.314160] attempt to access beyond end of device
[ 9869.314164] sdc: rw=0, want=625153217, limit=625142448
[ 9869.314414] attempt to access beyond end of device
[ 9869.314418] sdc: rw=0, want=625153218, limit=625142448
[ 9869.314660] attempt to access beyond end of device
[ 9869.314664] sdc: rw=0, want=625153219, limit=625142448
[ 9869.314911] attempt to access beyond end of device
[ 9869.314915] sdc: rw=0, want=625153220, limit=625142448
[ 9869.315157] attempt to access beyond end of device
[ 9869.315161] sdc: rw=0, want=625153221, limit=625142448
[ 9869.315462] attempt to access beyond end of device
[ 9869.315466] sdc: rw=0, want=625153222, limit=625142448
[ 9869.315708] attempt to access beyond end of device
[ 9869.315712] sdc: rw=0, want=625153223, limit=625142448
[ 9869.315951] attempt to access beyond end of device
[ 9869.315955] sdc: rw=0, want=625153216, limit=625142448
[ 9869.316197] attempt to access beyond end of device
[ 9869.316201] sdc: rw=0, want=625153217, limit=625142448
[ 9869.316438] attempt to access beyond end of device
[ 9869.316442] sdc: rw=0, want=625153218, limit=625142448
[ 9869.316685] attempt to access beyond end of device
[ 9869.316688] sdc: rw=0, want=625153219, limit=625142448
[ 9869.316926] attempt to access beyond end of device
[ 9869.316930] sdc: rw=0, want=625153220, limit=625142448
[ 9869.317172] attempt to access beyond end of device
[ 9869.317176] sdc: rw=0, want=625153221, limit=625142448
[ 9869.317414] attempt to access beyond end of device
[ 9869.317418] sdc: rw=0, want=625153222, limit=625142448
[ 9869.317662] attempt to access beyond end of device
[ 9869.317666] sdc: rw=0, want=625153223, limit=625142448
[ 9869.317919] attempt to access beyond end of device
[ 9869.317923] sdc: rw=0, want=625153392, limit=625142448
[ 9869.318164] attempt to access beyond end of device
[ 9869.318168] sdc: rw=0, want=625153393, limit=625142448
[ 9869.318407] attempt to access beyond end of device
[ 9869.318411] sdc: rw=0, want=625153394, limit=625142448
[ 9869.318674] attempt to access beyond end of device
[ 9869.318678] sdc: rw=0, want=625153395, limit=625142448
[ 9869.318917] attempt to access beyond end of device
[ 9869.318920] sdc: rw=0, want=625153396, limit=625142448
[ 9869.319187] attempt to access beyond end of device
[ 9869.319191] sdc: rw=0, want=625153397, limit=625142448
[ 9869.319451] attempt to access beyond end of device
[ 9869.319455] sdc: rw=0, want=625153398, limit=625142448
[ 9869.319695] attempt to access beyond end of device
[ 9869.319699] sdc: rw=0, want=625153399, limit=625142448
[ 9869.319938] attempt to access beyond end of device
[ 9869.319942] sdc: rw=0, want=625153392, limit=625142448
[ 9869.320186] attempt to access beyond end of device
[ 9869.320190] sdc: rw=0, want=625153393, limit=625142448
[ 9869.320431] attempt to access beyond end of device
[ 9869.320434] sdc: rw=0, want=625153394, limit=625142448
[ 9869.320437] attempt to access beyond end of device
[ 9869.320440] sdc: rw=0, want=625153395, limit=625142448
[ 9869.320442] attempt to access beyond end of device
[ 9869.320444] sdc: rw=0, want=625153396, limit=625142448
[ 9869.320446] attempt to access beyond end of device
[ 9869.320448] sdc: rw=0, want=625153397, limit=625142448
[ 9869.320451] attempt to access beyond end of device
[ 9869.320453] sdc: rw=0, want=625153398, limit=625142448
[ 9869.320455] attempt to access beyond end of device
[ 9869.320457] sdc: rw=0, want=625153399, limit=625142448
[ 9869.321876] attempt to access beyond end of device
[ 9869.321880] sdc: rw=0, want=625153408, limit=625142448
[ 9869.321883] attempt to access beyond end of device
[ 9869.321885] sdc: rw=0, want=625153409, limit=625142448
[ 9869.321887] attempt to access beyond end of device
[ 9869.321889] sdc: rw=0, want=625153410, limit=625142448
[ 9869.321893] attempt to access beyond end of device
[ 9869.321895] sdc: rw=0, want=625153408, limit=625142448
[ 9869.321897] attempt to access beyond end of device
[ 9869.321899] sdc: rw=0, want=625153409, limit=625142448
[ 9869.321902] attempt to access beyond end of device
[ 9869.321904] sdc: rw=0, want=625153410, limit=625142448
[ 9869.321911] attempt to access beyond end of device
[ 9869.321914] sdc: rw=0, want=625153408, limit=625142448
[ 9869.321916] attempt to access beyond end of device
[ 9869.321918] sdc: rw=0, want=625153409, limit=625142448
[ 9869.321921] attempt to access beyond end of device
[ 9869.321923] sdc: rw=0, want=625153410, limit=625142448
[ 9869.321930] attempt to access beyond end of device
[ 9869.321933] sdc: rw=0, want=625153408, limit=625142448
[ 9869.325610] attempt to access beyond end of device
[ 9869.325621] sdc: rw=0, want=625153409, limit=625142448
[ 9869.325626] attempt to access beyond end of device
[ 9869.325629] sdc: rw=0, want=625153410, limit=625142448
[ 9869.325660] attempt to access beyond end of device
[ 9869.325663] sdc: rw=0, want=625153408, limit=625142448
[ 9869.325665] attempt to access beyond end of device
[ 9869.325667] sdc: rw=0, want=625153409, limit=625142448
[ 9869.325670] attempt to access beyond end of device
[ 9869.325672] sdc: rw=0, want=625153410, limit=625142448
[ 9869.326753] attempt to access beyond end of device
[ 9869.326757] sdc: rw=0, want=625153408, limit=625142448
[ 9869.326760] attempt to access beyond end of device
[ 9869.326762] sdc: rw=0, want=625153409, limit=625142448
[ 9869.326764] attempt to access beyond end of device
[ 9869.326767] sdc: rw=0, want=625153410, limit=625142448
[ 9869.326775] attempt to access beyond end of device
[ 9869.326777] sdc: rw=0, want=625153408, limit=625142448
[ 9869.326780] attempt to access beyond end of device
[ 9869.326782] sdc: rw=0, want=625153409, limit=625142448
[ 9869.326784] attempt to access beyond end of device
[ 9869.326786] sdc: rw=0, want=625153410, limit=625142448
[ 9869.326799] attempt to access beyond end of device
[ 9869.326801] sdc: rw=0, want=625153344, limit=625142448
[ 9869.326804] attempt to access beyond end of device
[ 9869.326806] sdc: rw=0, want=625153345, limit=625142448
[ 9869.326809] attempt to access beyond end of device
[ 9869.326811] sdc: rw=0, want=625153346, limit=625142448
[ 9869.326813] attempt to access beyond end of device
[ 9869.326815] sdc: rw=0, want=625153347, limit=625142448
[ 9869.326818] attempt to access beyond end of device
[ 9869.326820] sdc: rw=0, want=625153348, limit=625142448
[ 9869.326823] attempt to access beyond end of device
[ 9869.326825] sdc: rw=0, want=625153349, limit=625142448
[ 9869.326827] attempt to access beyond end of device
[ 9869.326829] sdc: rw=0, want=625153350, limit=625142448
[ 9869.326832] attempt to access beyond end of device
[ 9869.326834] sdc: rw=0, want=625153351, limit=625142448
[ 9869.326844] attempt to access beyond end of device
[ 9869.326846] sdc: rw=0, want=625153400, limit=625142448
[ 9869.326849] attempt to access beyond end of device
[ 9869.326851] sdc: rw=0, want=625153401, limit=625142448
[ 9869.326854] attempt to access beyond end of device
[ 9869.326856] sdc: rw=0, want=625153402, limit=625142448
[ 9869.326858] attempt to access beyond end of device
[ 9869.326860] sdc: rw=0, want=625153403, limit=625142448
[ 9869.326863] attempt to access beyond end of device
[ 9869.326865] sdc: rw=0, want=625153404, limit=625142448
[ 9869.326868] attempt to access beyond end of device
[ 9869.326870] sdc: rw=0, want=625153405, limit=625142448
[ 9869.326872] attempt to access beyond end of device
[ 9869.326874] sdc: rw=0, want=625153406, limit=625142448
[ 9869.326877] attempt to access beyond end of device
[ 9869.326879] sdc: rw=0, want=625153407, limit=625142448
[ 9869.326886] attempt to access beyond end of device
[ 9869.326888] sdc: rw=0, want=625153408, limit=625142448
[ 9869.326891] attempt to access beyond end of device
[ 9869.326893] sdc: rw=0, want=625153409, limit=625142448
[ 9869.326895] attempt to access beyond end of device
[ 9869.326897] sdc: rw=0, want=625153410, limit=625142448
[ 9869.326904] attempt to access beyond end of device
[ 9869.326907] sdc: rw=0, want=625153408, limit=625142448
[ 9869.326909] attempt to access beyond end of device
[ 9869.326911] sdc: rw=0, want=625153409, limit=625142448
[ 9869.326914] attempt to access beyond end of device
[ 9869.326916] sdc: rw=0, want=625153410, limit=625142448
```

---

### Post by stephen53 on 2008-05-30
I once had a problem like this. Check to see what groups you belong to. Open a terminal and type groups. This will tell what groups you belong to. My groups are :

 adm disk dialout fax cdrom floppy tape audio dip video plugdev users lpadmin scanner admin

You may not belong to cdrom or plugdev. These groups are different from when I was running Dapper. Most likely you have a permission problem. You can add yourself to a group by opening up the gui 
administration/users and groups and add your self to the missing group you need. You can directly add yourself by editing /etc/groups as root or sudo. Here add your log in name to the group needed. This file is a list. Type a  , first if your name is not the first on that groups list. 

I hope this helps.

---

### Post by Lemon on 2008-06-04
That doesn't seem to be the problem. Im member of the following groups:

**haldaemon adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare ubuntuuser**

---


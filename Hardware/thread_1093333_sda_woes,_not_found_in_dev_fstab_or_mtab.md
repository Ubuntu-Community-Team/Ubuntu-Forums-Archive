---
title: "sda woes, not found in /dev fstab or mtab"
date: 2009-03-11
forum: Hardware
---

### Post by bearchild on 2009-03-11
I was running Windows XP on my PC, and for some reason it crashes (not a rare occurrence, haha). After finding no other alternative, I turn off the PC using the power button on the front of the case. I reboot, and it greets me with the phrase:

"Error could not load operating system"

D:

I then load up Crunchbang Linux 8.10, an ubuntu derivative and attempt to assess the problem. Here is the reading from dmesg dev | grep sda : 

```
[    4.400480] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.400507] sd 2:0:0:0: [sda] Write Protect is off
[    4.400511] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.400555] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.400643] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.400668] sd 2:0:0:0: [sda] Write Protect is off
[    4.400671] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.400714] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.400720]  sda:<6>usb 2-2: configuration #1 chosen from 1 choice
[  186.009805] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  186.009810] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  186.009833] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[  186.009839] end_request: I/O error, dev sda, sector 0
[  186.009900] Buffer I/O error on device sda, logical block 0
[  186.010127] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  367.630000] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  367.630004] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  367.630026] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[  367.630031] end_request: I/O error, dev sda, sector 0
[  367.630103] Buffer I/O error on device sda, logical block 0
[  367.630226] sd 2:0:0:0: [sda] Write Protect is off
[  367.630229] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  549.258527] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  549.258532] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  549.258556] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[  549.258561] end_request: I/O error, dev sda, sector 0
[  549.258636] Buffer I/O error on device sda, logical block 0
[  549.258763] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  730.883240] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  730.883245] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  730.883268] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[  730.883273] end_request: I/O error, dev sda, sector 0
[  730.883279] Buffer I/O error on device sda, logical block 0
[  730.883342] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  730.884569] sd 2:0:0:0: [sda] Write Protect is off
[  730.884576] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  912.500726] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  912.500731] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  912.500754] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[  912.500759] end_request: I/O error, dev sda, sector 0
[  912.500765] Buffer I/O error on device sda, logical block 0
[  912.503024] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1094.106311] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1094.106316] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 1094.106339] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[ 1094.106344] end_request: I/O error, dev sda, sector 0
[ 1094.106350] Buffer I/O error on device sda, logical block 0
[ 1094.107283] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1184.959451] sd 2:0:0:0: [sda] Write Protect is off
[ 1184.959461] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1184.960020] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1184.960384] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1184.960681] sd 2:0:0:0: [sda] Write Protect is off
[ 1184.960689] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1184.961112] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1184.961882] Dev sda: unable to read RDB block 0
[ 1366.595238] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1366.595243] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 1366.595266] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[ 1366.595271] end_request: I/O error, dev sda, sector 24
[ 1366.595277] Buffer I/O error on device sda, logical block 3
[ 1366.595457] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1548.218415] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1548.218421] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 1548.218443] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[ 1548.218448] end_request: I/O error, dev sda, sector 24
[ 1548.218455] Buffer I/O error on device sda, logical block 3
[ 1548.218519] sd 2:0:0:0: [sda] Write Protect is off
[ 1548.218523] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1548.223391] sd 2:0:0:0: [sda] Attached SCSI disk
[ 1548.228090] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1548.234248] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1548.234657] sd 2:0:0:0: [sda] Write Protect is off
[ 1548.234665] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1548.235109] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1729.883449] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1729.883455] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 1729.883477] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[ 1729.883482] end_request: I/O error, dev sda, sector 0
[ 1729.883488] Buffer I/O error on device sda, logical block 0
[ 1729.883498] Buffer I/O error on device sda, logical block 1
[ 1729.883502] Buffer I/O error on device sda, logical block 2
[ 1729.883506] Buffer I/O error on device sda, logical block 3
[ 1729.884927] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1911.518386] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1911.518392] sd 2:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 1911.518414] sd 2:0:0:0: [sda] Add. Sense: No additional sense information
[ 1911.518420] end_request: I/O error, dev sda, sector 0
[ 1911.518427] Buffer I/O error on device sda, logical block 0
[ 1911.518496] sd 2:0:0:0: [sda] Write Protect is off
[ 1911.518499] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1911.520074] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1911.520285] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1911.520433] sd 2:0:0:0: [sda] Write Protect is off
[ 1911.520438] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1911.520646] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

I tried lsscsi, here's the output for that:
```
[0:0:0:0]    cd/dvd  _NEC     DVD_RW ND-3540A  1.01  -       
[2:0:0:0]    disk    ATA      MAXTOR STM316081 3.AA  -
```

I know that my HDD is a Maxtor, so this at least shows that Linux can 'see' the HDD. There's no entry for it in fstab or mtab, and no "sda" in /dev . I hoped to use Ubuntu to wipe the disk and/or fsck it, but mounting it seems to be the main trouble here. Any ideas?

---

### Post by cariboo on 2009-03-11
It sounds like you have a hard drive that is going bad. I would suggest going to Maxtors web site and downloading the diagnostic tools and run them on your hard drive. I stopped using Maxtor drives several years ago, but there was a utility to re-certify the drive that saved my butt several times. :)

Jim

---


---
title: "DVD read issues"
date: 2008-10-05
forum: Hardware
---

### Post by ARhere on 2008-10-05
I am having an odd issue with my DVD+R optical drive reading and writing.  Even though I think both issues are related, I will post the write issue in a separate thread [so please check it out.]("http://ubuntuforums.org/showthread.php?p=5914551#post5914551")

When I place a burned DVD disk in my drive, Ubuntu does not auto mount it.  I tried two different types and same result for both.  One is a Memorex 16x DVD+R and the other is a SONY 16x DVD+R.  I tried to automatically mount it and **dmesg | tail** gives me...
```
andrew@GamePC:~$ sudo mount -vt iso9660 /dev/dvd2 /home/andrew/Desktop/CDROM/
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

andrew@GamePC:~$ dmesg | tail
[17326.204434] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[17326.204441] end_request: I/O error, dev sr0, sector 0
[17326.204448] Buffer I/O error on device sr0, logical block 0
[17331.799576] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[17331.799588] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[17331.799595] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[17331.799602] end_request: I/O error, dev sr0, sector 0
[17331.799608] Buffer I/O error on device sr0, logical block 0
[17348.294066] ISOFS: Unable to identify CD-ROM format.
[17438.864695] ISOFS: Unable to identify CD-ROM format.
```

I was able to manually mount them using the **-t udf**, but what is odd is I tried an older disk which is a Memorex 8x DVD+R and it automatically mounted them with iso9660.

What gives?  The older disk is the exact same brand, just 8x.  The 16x Memorex was burned in Vista, and the other two I cannot remember.  The results are the same in both my internal DVD-RW and my USB DVD-RW.

-AR

---


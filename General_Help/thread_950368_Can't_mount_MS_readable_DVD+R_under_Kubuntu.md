---
title: "Can't mount MS readable DVD+R under Kubuntu"
date: 2008-10-17
forum: General Help
---

### Post by mibadt on 2008-10-17
Hi,
My KUbuntu (8.0.4.1) won't mount 2 VD+R media  units which are fully readable by the same hardware under XP.

Naturally, other than that, the same drive works fine under Kubuntu. 
I don't know how these DVDs were burned, they contain lot of jpg files my daughter has burnt in Mongolia (not personally, she went into a local shop), while ravelling, and sent me by mail.

Please advise!

TIA

Michael Badt


As root I type:
root@Miki-Desk:/home/miki/hadar_temo# mount /media/cdrom0

I get the following:
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
-----------
Out of dmesg | tail

root@Miki-Desk:/home/miki/hadar_temo# dmesg | tail
[36851.005143] sr 4:0:1:0: [sr1] Add. Sense: CIRC unrecovered error
[36851.005151] end_request: I/O error, dev sr1, sector 4607376
[36851.005158] Buffer I/O error on device sr1, logical block 575922
[36859.574477] sr 4:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[36859.574488] sr 4:0:1:0: [sr1] Sense Key : Medium Error [current]root@Miki-Desk# mount /media/cdrom0
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@Miki-Desk:/home/miki/hadar_temo# dmesg | tail
[36851.005143] sr 4:0:1:0: [sr1] Add. Sense: CIRC unrecovered error
[36851.005151] end_request: I/O error, dev sr1, sector 4607376
[36851.005158] Buffer I/O error on device sr1, logical block 575922
[36859.574477] sr 4:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[36859.574488] sr 4:0:1:0: [sr1] Sense Key : Medium Error [current]
[36859.574495] sr 4:0:1:0: [sr1] Add. Sense: CIRC unrecovered error
[36859.574502] end_request: I/O error, dev sr1, sector 4607376
[36859.574509] Buffer I/O error on device sr1, logical block 575922
[36864.911378] UDF-fs: No VRS found
[36865.168336] ISOFS: Unable to identify CD-ROM format.

[36859.574495] sr 4:0:1:0: [sr1] Add. Sense: CIRC unrecovered error
[36859.574502] end_request: I/O error, dev sr1, sector 4607376
[36859.574509] Buffer I/O error on device sr1, logical block 575922
[36864.911378] UDF-fs: No VRS found
[36865.168336] ISOFS: Unable to identify CD-ROM format.

---

### Post by Pro-reason on 2008-10-17
This may be a known issue regarding a non-standard way of implementing UDF on DVDs.  However, I thought it affected Vista, not XP.

I remember seeing a complicated fix for it on the forums somewhere.

Burning them again may be a good solution.

---

### Post by niteshifter on 2008-10-17
Hi,

Installing the package udftools from the repos might help.

---

### Post by Pro-reason on 2008-10-17
[This other thread]("http://ubuntuforums.org/showthread.php?t=915797") may be informative.

---

### Post by mibadt on 2008-10-17
Thanks all,
Installing udftools still didn't help.
Michael Badt

---

### Post by niteshifter on 2008-10-17
Hi,

Sorry that udftools didn't work*. Follow the link Pro-reason gave, it should work. In the #15 post the steps are laid out a bit more clearly.


---
[ * Was hoping the repo version incorporated the patches like the current sourceforge version does. Apparently not. ]

---


---
title: "fdisk: unable to read /dev/sdc: Input/output error"
date: 2012-08-15
forum: Hardware
---

### Post by jiapei100 on 2012-08-15
Hi, all:

My 16Giga SD Card is now dead. Environment: Ubuntu 12.04

Phenomenon:
1)
```
pei@pei-GA-870A-UD3:/dev$ sudo fdisk /dev/sdc
fdisk: unable to read /dev/sdc: Input/output error
```

2)
```
pei@pei-GA-870A-UD3:/dev$ ls -l sd*
brw-rw---- 1 root disk 8,  0 Aug 15 02:39 sda
brw-rw---- 1 root disk 8,  1 Aug 15 01:17 sda1
brw-rw---- 1 root disk 8,  2 Aug 15 02:39 sda2
brw-rw---- 1 root disk 8,  5 Aug 15 01:17 sda5
brw-rw---- 1 root disk 8,  6 Aug 15 02:39 sda6
brw-rw---- 1 root disk 8, 16 Aug 15 02:39 sdb
brw-rw---- 1 root disk 8, 17 Aug 15 01:17 sdb1
brw-rw---- 1 root disk 8, 32 Aug 15 03:05 sdc
```
Only **sdc**, but no **sdc1**


3) GParted is not able to show details of **/dev/sdc**, namely, there is nothing related to **/dev/sdc**.

4) ```
cat /var/log/kern.log
``` gives
> Aug 15 03:39:36 pei-GA-870A-UD3 kernel: [ 8502.642244] sd 21:0:0:0: [sdc] Unhandled sense code
Aug 15 03:39:36 pei-GA-870A-UD3 kernel: [ 8502.642254] sd 21:0:0:0: [sdc]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
Aug 15 03:39:36 pei-GA-870A-UD3 kernel: [ 8502.642264] sd 21:0:0:0: [sdc]  Sense Key : Medium Error [current] 
Aug 15 03:39:36 pei-GA-870A-UD3 kernel: [ 8502.642274] sd 21:0:0:0: [sdc]  Add. Sense: Unrecovered read error
Aug 15 03:39:36 pei-GA-870A-UD3 kernel: [ 8502.642285] sd 21:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Aug 15 03:39:36 pei-GA-870A-UD3 kernel: [ 8502.642305] end_request: critical target error, dev sdc, sector 0
Aug 15 03:39:36 pei-GA-870A-UD3 kernel: [ 8502.642315] Buffer I/O error on device sdc, logical block 0


Please do help to have my SD card come back to life.....

Cheers
Pei

---


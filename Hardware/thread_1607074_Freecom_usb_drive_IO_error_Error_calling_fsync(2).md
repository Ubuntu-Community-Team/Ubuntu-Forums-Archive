---
title: "Freecom usb drive I/O error: Error calling fsync(2)"
date: 2010-10-27
forum: Hardware
---

### Post by harmus on 2010-10-27
Hi,

I encrypted my Freecom XXS drive with Truecrypt. I could not mount the partition afterwards (with truecrypt), so I tried formatting the drive so I could use it again.

When i try to format it i get this error: 
Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdc: Input/output error

The drive worked well before this. I replaced the cable, didn't work. I'll see if I can find some windoze computer to see if it works over there.

If the sectors are bad, how do i mark them bad? I'm not a very experienced ubuntu user yet.

dmesg gives:

[ 1217.368765] sd 4:0:0:0: [sdc] Unhandled error code
[ 1217.368769] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1217.368772] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 00 00 00 00 00 00 f0 00
[ 1217.368782] end_request: I/O error, dev sdc, sector 0
[ 1217.368786] quiet_error: 54 callbacks suppressed
[ 1217.368788] Buffer I/O error on device sdc, logical block 0
[ 1217.368790] lost page write due to I/O error on sdc
[ 1217.368798] Buffer I/O error on device sdc, logical block 1
[ 1217.368799] lost page write due to I/O error on sdc
[ 1217.368802] Buffer I/O error on device sdc, logical block 2
[ 1217.368804] lost page write due to I/O error on sdc
[ 1217.368807] Buffer I/O error on device sdc, logical block 3
[ 1217.368808] lost page write due to I/O error on sdc
[ 1217.368811] Buffer I/O error on device sdc, logical block 4
[ 1217.368813] lost page write due to I/O error on sdc
[ 1217.368815] Buffer I/O error on device sdc, logical block 5
[ 1217.368817] lost page write due to I/O error on sdc
[ 1217.368820] Buffer I/O error on device sdc, logical block 6
[ 1217.368821] lost page write due to I/O error on sdc
[ 1217.368824] Buffer I/O error on device sdc, logical block 7
[ 1217.368825] lost page write due to I/O error on sdc
[ 1217.368828] Buffer I/O error on device sdc, logical block 8
[ 1217.368830] lost page write due to I/O error on sdc
[ 1217.368832] Buffer I/O error on device sdc, logical block 9
[ 1217.368834] lost page write due to I/O error on sdc
[ 1217.371878] sd 4:0:0:0: [sdc] Unhandled error code
[ 1217.371880] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1217.371883] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 00 00 00 f0 00 00 10 00
[ 1217.371891] end_request: I/O error, dev sdc, sector 240
[ 1217.393638] sd 4:0:0:0: [sdc] Unhandled error code
[ 1217.393642] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1217.393647] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 12 a1 9d b0 00 00 f0 00
[ 1217.393660] end_request: I/O error, dev sdc, sector 312581552
[ 1217.396127] sd 4:0:0:0: [sdc] Unhandled error code
[ 1217.396130] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1217.396134] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 12 a1 9e a0 00 00 08 00
[ 1217.396143] end_request: I/O error, dev sdc, sector 312581792

Thanks for any reply.

---


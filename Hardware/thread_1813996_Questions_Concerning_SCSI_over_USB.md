---
title: "Questions Concerning SCSI over USB"
date: 2011-07-28
forum: Hardware
---

### Post by iwoloschin on 2011-07-28
Hi everyone,

I'm trying to develop a USB CD-ROM Emulator, using an Atmel AVR to read an ISO file off of a SD Card, and tricking the computer into thinking it's a CD-ROM.  I'm doing some debugging using Wireshark on Ubuntu (Lucid), and I'm having trouble getting the computer to read any sectors.  Under Wireshark I can see that SCSI Read (10) commands are being passed, and successfully returning 2048 byte blocks of the ISO file, but Ubuntu is having trouble interpreting the data.

From dmesg:

[171882.969759] sr 22:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[171882.969768] end_request: I/O error, dev sr1, sector 0
[171882.969772] Buffer I/O error on device sr1, logical block 0
[171882.969775] Buffer I/O error on device sr1, logical block 1
[171882.969780] Buffer I/O error on device sr1, logical block 2
[171882.969782] Buffer I/O error on device sr1, logical block 3
[171882.969785] Buffer I/O error on device sr1, logical block 4
[171882.969787] Buffer I/O error on device sr1, logical block 5
[171882.969790] Buffer I/O error on device sr1, logical block 6
[171882.969792] Buffer I/O error on device sr1, logical block 7
[171883.067745] sr 22:0:0:0: [sr1] Unhandled error code
[171883.067748] sr 22:0:0:0: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[171883.067751] sr 22:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[171883.067759] end_request: I/O error, dev sr1, sector 0
[171883.067762] Buffer I/O error on device sr1, logical block 0
[171883.067765] Buffer I/O error on device sr1, logical block 1

I'm not sure where else to troubleshoot this, clearly I'm doing something wrong, I can't imagine this is Ubuntu's fault, but I wanted to ask here in case there are weird behaviors that Ubuntu expects with a USB (SCSI) CD-ROM.

Thanks!

---


---
title: "Buffer I/O error on device ... logical block ..."
date: 2010-06-02
forum: Hardware
---

### Post by Albretch Mueller on 2010-06-02
~ 
 I have some 1980 data on DVDs I would like to back up to a hard drive
~ 
 The data itself is apparently mounted read only and I can access and see it with no problems
~ 
 The thing is that when I try to copy it do my hard drive large files are not being copied (only smaller ones) and this is what I see when I run dmesg
~ 
```

ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
UDF-fs: Partition marked readonly; forcing readonly mount
UDF-fs INFO UDF: Mounting volume 'DATA_DISK01', timestamp 2000/10/03 18:41 (1000)
sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
end_request: I/O error, dev sr0, sector 21044
Buffer I/O error on device sr0, logical block 5261
Buffer I/O error on device sr0, logical block 5262
Buffer I/O error on device sr0, logical block 5263
Buffer I/O error on device sr0, logical block 5264
Buffer I/O error on device sr0, logical block 5265
Buffer I/O error on device sr0, logical block 5266
Buffer I/O error on device sr0, logical block 5267
Buffer I/O error on device sr0, logical block 5268
sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
end_request: I/O error, dev sr0, sector 21044
Buffer I/O error on device sr0, logical block 5261
Buffer I/O error on device sr0, logical block 5262
sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
end_request: I/O error, dev sr0, sector 197936
. . .

```~ 
 How can I troubleshoot this problems?
~
 Thanks
 lbrtchx

---


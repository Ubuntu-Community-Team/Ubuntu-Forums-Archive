---
title: "External hd reiserfs formatted doesn't work"
date: 2009-01-27
forum: Hardware
---

### Post by bubu7 on 2009-01-27
Hallo,
I can't see external hd, formatted with reiserfs. It worked well since yesterday. if i do fdisk -l, i can see the disk that works, and the program doesn't go away; I have to interrupt it.
if i do dmesg | tail I have this output:
"REISERFS warning (device sdc1): sh-2022 reiserfs_fill_super: unable to initialize journal space
REISERFS warning (device sdc2): super-6502 reiserfs_getopt: unknown mount option "force"
sd 12:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 240991081
REISERFS warning (device sdc2): sh-2006 read_super_block: bread failed (dev sdc2, block 2, size 4096)
sd 12:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 240991193
REISERFS warning (device sdc2): sh-2006 read_super_block: bread failed (dev sdc2, block 16, size 4096)
REISERFS warning (device sdc2): sh-2021 reiserfs_fill_super: can not find reiserfs on sdc2
usb 1-1.3: USB disconnect, address 13"
Can someone helps me ?  Thanks in advance,

---


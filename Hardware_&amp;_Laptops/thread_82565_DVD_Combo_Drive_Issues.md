---
title: "DVD Combo Drive Issues"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by ecletrik on 2005-10-26
I have a Writemaster DVD combo drive that will read CD's just fine after a fresh Ubuntu 5.10 installation.

However, when I put a DVD(no scratches or anything, works on windows fine) in the drive, it will show me what is on it, but when i drag and drop one of the files, it will say "I/O ERROR RETRY CANCEL SKIP".

Please help me fix this :(


ecletrik@ecletrik:~$ dmesg
8000] end_request: I/O error, dev hdc, sector 88948
[4294905.408000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[4294905.408000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[4294905.408000] ide: failed opcode was: unknown
[4294905.408000] end_request: I/O error, dev hdc, sector 88952
[4294905.409000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[4294905.409000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[4294905.409000] ide: failed opcode was: unknown

---


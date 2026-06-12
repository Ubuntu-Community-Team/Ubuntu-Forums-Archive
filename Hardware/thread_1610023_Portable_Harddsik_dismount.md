---
title: "Portable Harddsik dismount"
date: 2010-10-31
forum: Hardware
---

### Post by craphunter on 2010-10-31
Hi,

I do habe ubunt 10.10. My protable harddisk ist dismounting when I am playing mp3 after 10, 15 minutes. I took a look in log-files, here it is:

Oct 31 11:12:29 gumble kernel: [ 4803.184043] sd 6:0:0:0: Device offlined - not ready after error recovery
Oct 31 11:12:29 gumble kernel: [ 4803.184063] sd 6:0:0:0: [sdb] Unhandled error code
Oct 31 11:12:29 gumble kernel: [ 4803.184068] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Oct 31 11:12:29 gumble kernel: [ 4803.184075] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 15 d0 15 27 00 00 f0 00
Oct 31 11:12:29 gumble kernel: [ 4803.184278] sd 6:0:0:0: [sdb] Unhandled error code
Oct 31 11:12:29 gumble kernel: [ 4803.184282] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Oct 31 11:12:29 gumble kernel: [ 4803.184306] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 15 d0 16 17 00 00 10 00


Anybody has an idea?

TIA

Craphunter

---


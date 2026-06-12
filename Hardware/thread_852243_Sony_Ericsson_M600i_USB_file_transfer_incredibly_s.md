---
title: "Sony Ericsson M600i: USB file transfer incredibly slow"
date: 2008-07-07
forum: Hardware
---

### Post by zweistein on 2008-07-07
I recently bought a new M2 card for my Sony Ericsson M600i mobile phone, and I'd like to use it as an MP3 player. I'm using the USB cable I got with the phone (I don't have Bluetooth on my laptop), but the transfer is incredibly slow (around 10-15 minutes for 100 MB).

I noticed the following lines in dmesg during the file transfers:
```
[ 2389.969689] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 2389.969707] end_request: I/O error, dev sdb, sector 4025

```

These show up periodically in the list.

At first, the transfer works just fine - it manages to transfer around 25 MB, and then it simply stops for some time, and then starts again etc.

My phone is in the File Transfer mode while connected to the PC.

Any ideas about the cause and the fix? I'm using Ubuntu 8.04.1 with the 2.6.24-19 kernel.

Thanks!

---

### Post by moron on 2008-10-06
Howdy.  In my case I have a Sansa View which is displaying a similar issue though so far I have not been able to find any obvious errors in the logs. 

Sorry I don't have a solution yet but I share your pain here.

=)

Cheers

---


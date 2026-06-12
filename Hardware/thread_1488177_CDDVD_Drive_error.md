---
title: "CD/DVD Drive error"
date: 2010-05-19
forum: Hardware
---

### Post by p252 on 2010-05-19
Has anyone experienced this problem? I've had it since the 2.6.31.* kernels and it's not just Ubuntu. I'm running 10.04 LTS (which is awesome) but the problem still remains. Whatever it is wreaks havoc with my optical drive and renders it worthless for the most part. However, the problem seems to be related to CD's; when I put a DVD disc in I do not get the same problem. I am running a Dell Inspiron 1420 laptop. Here is what the syslog has to say:

May 19 17:21:48 rukia kernel: [  395.189431] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 19 17:21:48 rukia kernel: [  395.189439] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May 19 17:21:48 rukia kernel: [  395.189450] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
May 19 17:21:48 rukia kernel: [  395.189463] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
May 19 17:21:48 rukia kernel: [  395.189487] end_request: I/O error, dev sr0, sector 0

---


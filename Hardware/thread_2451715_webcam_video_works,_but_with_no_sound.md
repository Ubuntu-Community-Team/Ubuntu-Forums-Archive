---
title: "webcam video works, but with no sound"
date: 2020-10-09
forum: Hardware
---

### Post by jfca283 on 2020-10-09
Hello, 
I boght a webcam with mic included.
When I run this, I see the webcam with no name
```
lsb_release -a; uname -a; lsusb
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.5 LTS
Release:	18.04
Codename:	bionic
Linux juan-OptiPlex-7010 4.15.0-118-generic #119-Ubuntu SMP Tue Sep 8 12:30:01 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
Bus 002 Device 003: ID 214b:7250  
Bus 002 Device 007: ID 1224:2a25  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0458:6001 KYE Systems Corp. (Mouse Systems) GF3000F Ethernet Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I googled and found out that Bus 002 Device 007: ID 1224:2a25  is my webcam.
If I go to sound setting, I can see the mic as the png file shows.
I have no idea what to do. I went to alsamixer using the terminal, and I set all the volume options up.
Can you guide me?
I need the webcam to work...

---


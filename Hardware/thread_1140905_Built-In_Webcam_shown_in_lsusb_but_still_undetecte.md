---
title: "Built-In Webcam shown in lsusb but still undetected by programs"
date: 2009-04-28
forum: Hardware
---

### Post by David85 on 2009-04-28
Hey all!
I just installed Ubuntu for the first time and by and large I'm more than pleased with it. I've found many solutions to problems in this forum for which I'm very grateful. I haven't been able, however, to cope with this issue with my built-in webcam. I am running Ubuntu 9.04 64bit on a Toshiba U405 (amd64) and this is the output of lsusb:

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

AFAIK, the "Chicony" line means that my webcam is "somehow" recognized by the system. However, programs such as Camorama show this message: "Could not connect to video device (/dev/video0)". I've checked the /dev directory for other "video*" with no luck. Maybe it's got something to do with the webcam being the 003 device in the 001 bus? I'm a total newbie to linux so any kind of feedback would be more than welcome.
Thank you very much and please do let me know if any other specs or data is needed.

Regards,
David

---

### Post by rajamouli2000 on 2009-04-28
I have jaunty installed on my Toshiba m300. 
I use cheese, works like a charm. Can shoot pictures and videos. 
```
sudo apt-get install cheese
```

---

### Post by David85 on 2009-04-28
All I get are the color bars... No webcam image at all :S

---

### Post by Rarensu on 2009-07-07
I'm running Ubuntu 9.04 / Jaunty on a Toshiba Satellite L335D-S7901.

lsusb returns, among other things:
Bus 002 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd

Camorama presents error:
"could not connect to video device (/dev/video0)"

Cheese, however, runs fine.

What's the difference?

---


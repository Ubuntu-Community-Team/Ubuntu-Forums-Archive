---
title: "Acer 4920 with problem webcam and wireless on Intrepid"
date: 2008-11-25
forum: Hardware
---

### Post by supriyanto on 2008-11-25
Dear Ubuntuers, ;)

I have some problem with Ubuntu 8.10 on my Acer 4920.  First with Suyin Webcam on cheese application, and second with problem wireless up-down.

The first time I ran Cheese, it worked great until I clicked the "effects" button. Then it crashed and I had to force-quit it.

Now whenever I run cheese, it just sits at a Gnome Foot sticking out its toes. I'm lucky with the foot disappears, and I get my picture webcam on there. But, when I click button effect and close from that effect, I get a grey screen on cheese is hang. And also nothing video can be I capture with this program. Why this can be happen and how to fix this problem? For information, when I used Ubuntu 8.04, this program can be work properly.

I also have problems with wireless drivers on this notebook with Intrepid. This device actually is working properly at the Intrepid. But why this wireless can't up again when I press button Wireless on this laptop? I tried to press button Wireless again to up wireless network, but still can't up. When I reboot my PC this wireless can be up again, Is there any parameter or some way to fix this problem?


For information, this is my Acer 4920 spesification:
ASPIRE 4920
Intel Core 2 Duo Processor T5550
14.1 WXGA Acer CrystalBrite LCD
Mobile Intel Graphics X3100
1.5 GB RAM DDR2
160 GB

For information, this is the results from lsub:
```
$ lsusb
Bus 003 Device 002: ID 064e:a101 Suyin Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
```

$ lspci
...
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
...
```

Please help me to solve this problem.

Thanks.

---


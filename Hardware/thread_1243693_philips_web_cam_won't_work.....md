---
title: "philips web cam won't work...."
date: 2009-08-18
forum: Hardware
---

### Post by badman35 on 2009-08-18
I hav a philips sic4700/37 webcam and i'm trying to get it to work on kubuntu 9.04 without any luck can someone on the forum give me a hand with this...

Here is what bash is telling me

```
root@ubuntu:~# sudo modprobe -r gspca
FATAL: Module gspca not found.
root@ubuntu:~# sudo lsmod | grep -i gspca
gspca_spca561          18944  0
gspca_main             29952  1 gspca_spca561
videodev               41600  1 gspca_main
root@ubuntu:~# sudo lsusb
Bus 001 Device 005: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 001 Device 004: ID 17d0:0116 Sanford L.P.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@ubuntu:~#

```

Hope this helps...

---


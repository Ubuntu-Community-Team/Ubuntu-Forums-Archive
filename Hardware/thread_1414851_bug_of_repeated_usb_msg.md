---
title: "bug of repeated usb msg"
date: 2010-02-24
forum: Hardware
---

### Post by ankscorek on 2010-02-24
helo friends here ar emy few outputs

ankush@ankush-laptop:~$ lsusb
Bus 002 Device 004: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 119: ID 12d1:140b Huawei Technologies Co., Ltd. 
Bus 003 Device 003: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




ankush@ankush-laptop:~$ luvcview
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such file or directory


ankush@ankush-laptop:~$ uname -a
Linux ankush-laptop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux


here is a snippet of my kernel.log

Feb 24 13:43:13 ankush-laptop kernel: [  399.702589] hub 3-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:13 ankush-laptop kernel: [  399.982554] hub 1-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:13 ankush-laptop kernel: [  400.246324] hub 3-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:14 ankush-laptop kernel: [  400.522544] hub 1-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:14 ankush-laptop kernel: [  400.802574] hub 3-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:14 ankush-laptop kernel: [  401.092607] hub 1-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:14 ankush-laptop kernel: [  401.356136] hub 3-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:15 ankush-laptop kernel: [  401.642592] hub 1-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:15 ankush-laptop kernel: [  401.902628] hub 3-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:15 ankush-laptop kernel: [  402.182762] hub 1-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:16 ankush-laptop kernel: [  402.452615] hub 3-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:16 ankush-laptop kernel: [  402.730805] hub 1-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:16 ankush-laptop kernel: [  402.990085] hub 3-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:16 ankush-laptop kernel: [  403.272759] hub 1-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:17 ankush-laptop kernel: [  403.532560] hub 3-0:1.0: unable to enumerate USB device on port 2
Feb 24 13:43:17 ankush-laptop kernel: [  403.812550] hub 1-0:1.0: unable to enumerate USB device on port 2

this annoying msg has made it hard for me to work in terminal ie mode without desktop enviornment

i am booting with the -noapci -nousb option turned on in my grub

kindly someone help me rectify this error and also to bring up my chicony webcam

thanx

ps i am using ubuntu karmic

ok the problem of booting is solved it was just my grub had got corrupted and i repaired it from the live CD

but the usb2 prob is still there and also i see that when i boot from grub without -apci

the lsusb output is

ankush@ankush-laptop:~$ lsusb
Bus 004 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 060: ID 12d1:140b Huawei Technologies Co., Ltd.
Bus 003 Device 075: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


in other words the webcam hardware is not detected

can someone please put me in the correct direction

---

### Post by ankscorek on 2010-02-27
ok after doing lot of reading i have finally arrived at the conclusion that i need a BIOS update...can someone please help me in this matter

i have no windows

i have ubuntu karmic

i have amd64

i have phoenix bios

quanta motherboard

f.04 is my bios version

---

### Post by IcarusR on 2010-02-27
I don't think a bios upgrade will resolve this 'bug'.
If you google 'unable to enumerate USB device' you will find numerous pages.
There are bug reports for several distros.

If you really want to update your bios then check this page out.

[http://macles.blogspot.com/2008/07/flashing-bios.html]("http://macles.blogspot.com/2008/07/flashing-bios.html")

Don't forget there is always a risk of 'bricking' anything when doing bios update.

---


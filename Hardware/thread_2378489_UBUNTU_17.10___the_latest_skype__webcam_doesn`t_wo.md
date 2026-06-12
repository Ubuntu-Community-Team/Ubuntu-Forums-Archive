---
title: "UBUNTU 17.10 /  the latest skype / webcam doesn`t work"
date: 2017-11-23
forum: Hardware
---

### Post by vicub on 2017-11-23
Dear all,

Please help or at least advice.
I`ve got old A4 TECH PK-336 MB web camera. It seems to me that Skype doesn`t see it. But the built-in sound works well. 

lsusb shows the following  

ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 Webcam

The result of command "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype" is:

ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD  cannot be preloaded (cannot open shared object file): ignored.

The result of command "LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype" is:

ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so'  from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32):  ignored.

Please help to fix it if it is possible. Or at least help me to understand why it happen.

 Linux vicub-GA-MA770T-UD3 4.13.0-17-generic #20-Ubuntu SMP Mon Nov 6 10:04:08 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

---


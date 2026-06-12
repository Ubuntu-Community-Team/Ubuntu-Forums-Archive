---
title: "[SOLVED] /dev/video0 gone???"
date: 2008-11-22
forum: General Help
---

### Post by DrDagostino1 on 2008-11-22
I had just tried to uninstall and then install a new driver for my webcam and then my /dev/video0 file disappeared. Does anyone know how to get it back/rebuild it? NEED HELP! I can't use any webcam until its fixed.
PS: Even with all my old webcam drivers reinstalled, it still won't work.

---

### Post by cariboo on 2008-11-22
What is the output of dmesg, when you plug your device in? To see the output, open a Applications-->Accessories-->Terminal and type:

```
tail -n 10 /var/log/dmesg
```

The above command will output the last 10 lines of dmesg. Could you paste them in your next post.

Jim

---

### Post by DrDagostino1 on 2008-11-22
[   42.899202] ov51x: probe of 1-4:1.0 failed with error -5
[   42.899227] usbcore: registered new interface driver ov51x
[   42.899230] /home/derek/Desktop/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: 1.5.9 : ov51x USB Camera Driver
[   42.899315] usbcore: registered new interface driver zd1211rw
[   42.975294] usbcore: registered new interface driver snd-usb-audio
[   43.139556] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   44.136068] lp: driver loaded but no devices found
[   44.264160] Adding 2168764k swap on /dev/sda3.  Priority:-1 extents:1 across:2168764k
[   44.800833] EXT3 FS on sda2, internal journal
[   45.910667] ip_tables: (C) 2000-2006 Netfilter Core Team

---

### Post by DrDagostino1 on 2008-11-22
I solved it! It was one last driver that was still installed, I uninstalled it and reinstalled everything and then it was fixed! Thanks though!

---


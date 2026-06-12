---
title: "WD external not recognized"
date: 2011-08-05
forum: Hardware
---

### Post by hellopasQualle on 2011-08-05
Hi everyone,

so since this is my first post here (actually I was pretty active a couple of year ago but can't remember my username/pw), I'd like to say hello. And I hope that you can help me with the following issue.

My dad (Win7 user) bought a Western Digital hard drive a year ago. I think it's an 320gb MyBook. He reported that it suddenly stopped working on his Win7 machine. Actually, there's a circular light on the front which is glowing if the drive is running. Well, now it isn't. Naive as I am, I said to him, that that's no problem, I'll get it working again and save him the data. So I dusted off my old ubuntu machine. Cos, if there's no other way, linux can do it. But enough with the babbling.

I plug it into the power supply, the light on the front isn't glowing, but I hear the drive running. Then I plug it in the usb port. Of course it won't be recognized.

Output of ```
lsusb
``` is:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 054c:0281 Sony Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
I'm not sure but I think the hard drive isn't recognized here. Or is it the Elan blahblah?
```
sudo fdisk -l
``` gives me:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xab72ab72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1948    15647278+  83  Linux
/dev/sda2            1949        9729    62500882+   5  Extended
/dev/sda5            1949        9364    59568988+  83  Linux
/dev/sda6            9365        9729     2931831   82  Linux swap / Solaris
```
Note that I have my /home on a separate partition.

Ok, now. I know Linux can do it. I think I kind of repaired a similar error on the hard drive of my flat mate a year ago. But of course I don't remember how I did it.

I would really appreciate if you would help me out here. I'll try to support you as good as my kind of nooby linux knowledge is capable of.

Thank you very much.
Cheers,

Pascal

Edit: Ah, and I really hope, there's something to save left, and you don't tell me that the hard drive is broken :)

---


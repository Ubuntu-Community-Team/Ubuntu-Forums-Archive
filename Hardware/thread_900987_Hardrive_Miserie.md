---
title: "Hardrive Miserie"
date: 2008-08-25
forum: Hardware
---

### Post by Rawton on 2008-08-25
Hello.
I am new to using Linux i tried red hat tthen went with ubuntu. Ubuntu is not accessing or reading my hot swappables, I have a power edge 4600 and i would like i to read the other drives i am hiving major difficulty please can anyone help me.

---

### Post by cariboo on 2008-08-26
We need a lot more information, how are your hot swapable drives set up, is it a raid array, jbod or something else. Please post the output of:

```
sudo fdisk -l
```

you'll have to do this in a Applications-->Accessories-->Terminal

Jim

---

### Post by Rawton on 2008-09-01
Disk /dev/sda: 36.4 GB, 36420075008 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59f1e0a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4240    34057768+  83  Linux
/dev/sda2            4241        4427     1502077+   5  Extended
/dev/sda5            4241        4427     1502046   82  Linux swap / Solaris
and it printed this over and over until it got to /dev/sdo1

---


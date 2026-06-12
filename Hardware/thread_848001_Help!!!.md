---
title: "Help!!!"
date: 2008-07-03
forum: Hardware
---

### Post by bboyghost on 2008-07-03
okay, i'm new to linux and was going through the install. at the end,just before it finished and error message popped up saying "error 5" something to do with my input output. i read up a bit and saw something on BIOS so i checked mine, didnt see the problem though... also saw something about running terminal and typing in sudo fdisk -l to help the person assisting so i did and heres the info that popped up...

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc20e3b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11785    94662981   83  Linux
/dev/sda2           11786       12161     3020220    5  Extended
/dev/sda5           11786       12161     3020188+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 



please help as i have no clue what else to do...

---

### Post by bboyghost on 2008-07-03
also, i am using a Sony vaio laptop, if that means anything to you guys

---

### Post by lisati on 2008-07-03
It's also a good idea to use a more descriptive title than "Help"

---

### Post by bboyghost on 2008-07-03
> **lisati said:**
> It's also a good idea to use a more descriptive title than "Help"

okay, but can you help at all?

---

### Post by raf952 on 2008-07-03
> **bboyghost said:**
> okay, but can you help at all?
You might consider reposting with the Subject, "Unable to install on Sony Vaio SZ645P2 laptop" -- it gives you a better chance of catching the attention of folks with experience with the issue, or have interest in laptops.

Also, carefully note the specific error message. You provide information about your hard drive but it's not clear whether your error has anything to do with it. Having details about your general machine config would be good: how much memory, what BIOS version, etc. might be helpful.

Just crying "Help" works only for damsels in distress... and you don't have the legs for that...

---


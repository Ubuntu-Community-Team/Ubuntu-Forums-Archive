---
title: "Problem w/ Maxtor OneTouch III"
date: 2010-12-12
forum: Hardware
---

### Post by sonatso on 2010-12-12
I am experiencing an unusual I/O error with a the drive mentioned. When I plug in the device, it is recognized, as the output from dmesg tells me. But any attempt to actually read or write information to it is useless. mkfs refuses to work with it because it has "not just one partition". So, use fdisk. Well, fdisk refuses to work with it: "Unable to read /dev/sdb".

Not even the brute force method works: dd merely cites an "Input/output error" and exits. 

I would think that it is a hardware error but for one thing: until upgrading to Windows 7 on another computer, the drive worked fine with XP. 7 refuses to work with it, so I tried to format it on Ubuntu, leading to my current conundrum. Any ideas?

---


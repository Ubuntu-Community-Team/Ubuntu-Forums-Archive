---
title: "Can't start any OS, help!!"
date: 2010-08-10
forum: Hardware
---

### Post by HiTmAnN on 2010-08-10
Hi, i have two OS in my laptop, windows 7 and ubuntu, each one in its own partition. I recently installed a software in windows 7, and now i can't start any SO, the System remains in a black screen and shows the following: 
"No module name found
aborted. Press any key to exit". After pressing a key shows:
"Broadcom UNDI PXE-2.1 v11.0.9
Copyright (C) 2000-2008 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
All rights reserved
PXE-E61: Media test failure, check cable
PXE-M0F: Exitin broadcom PXE ROM.
Operating Systiem not found"
I then started with a LiveCd of ubuntu and saw that the partitions names of ubuntu were changed, partitions / and /home specifically, so i changed their labels again, but didn't work.

Somebody could help me please?? Dunno what to do, i would be so grateful. And sorry 4 my english :)

---

### Post by cody1233 on 2010-08-11
Does it show any logo or anything when you turn it on? if yes, try grub because your bootloader got damaged...you can download a grub live cd [here]("http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/super_grub_disk_0.9799.iso")

---

### Post by HiTmAnN on 2010-08-11
Thanks for the help cody1233. 
My laptop is a Dell studio xps and when i turn on the computer it shows the Dell logo and have 2 options while the system loads, F2 for setup and F12 for boot options, the first leads me to the Bios setup and the second one leads me to choose boot options between: hard drive, cd/dvd drive, removable devices, diagnostic, and network. After that screen, it leads me to the screen described before.
So, that liveCd that you showed me, how does it work and for what?, would you bring me a link describing it please?
I thought starting whith the ubuntu LiveCd and modify the grub files, but would it be possible to update the grub in the partition?

---

### Post by HiTmAnN on 2010-08-12
I solved my problem reinstaling the grub, thanks for the help.

---


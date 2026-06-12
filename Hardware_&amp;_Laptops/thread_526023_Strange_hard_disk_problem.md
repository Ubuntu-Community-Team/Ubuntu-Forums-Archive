---
title: "Strange hard disk problem"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by antoant on 2007-08-15
Hello,

I am having a strange problem with one of my hard drives. I have a dual boot system with two hard drives. The master disk is 40GB and has the xubuntu 7.04 partition, the swap partition, and a fat32 partition on it. The slave hard drive has the windows xp ntfs partition on it. The problem is that I keep getting the following errors while xubuntu is loading.

[number that keeps changing] ata1.01: exception Emask 0x0 SAct ........
[number that keeps changing] ata1.01: (BMDMA stat 0x64 ...)
[number that keeps changing] ata1.01: cmd...........

Buffer I/O error on device sdb1, logical block 32
Buffer I/O error on device sdb1, logical block 33
Buffer I/O error on device sdb1, logical block 34
Buffer I/O error on device sdb1, logical block 35

The first three lines come up more often than the buffer lines and the buffer lines might not be 4 they might drop to 1 or any other number between 1 and 5 with different block numbers. I did not manage to write down the complete error that comes up (hence the many dots) but I will try again and edit this post.

Now seeing that the problem might be with the second disk I decided to disconnect it and see what happens. Indeed the problem went away without the second disk. I also tried to put the second disk on the second PATA channel put the error came up again.

This problem also happened when I was trying to install xubuntu on just the second disk so I know it also happens if I only have just that second disk in the PC. 

My PC is a Dell Optiplex GX150 with a P3-1.13GHz and 256MB ram, the north bridge chip is the i815 by Intel. The hard disks are old and do not have SMART capabilities.

Although this problem does not stop me from using xubuntu it makes loading the OS a 5 to 10 minute thing when it takes only a minute without the problem. Plus I would like to know if this means that my second drive is on the way out so I can save my data from the windows partition.

Thank you for your help and sorry about the long post

---


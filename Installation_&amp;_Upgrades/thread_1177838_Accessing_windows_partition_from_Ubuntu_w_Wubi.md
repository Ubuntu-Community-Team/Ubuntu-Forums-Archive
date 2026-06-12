---
title: "Accessing windows partition from Ubuntu w/ Wubi"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by shadowbound on 2009-06-03
Hey.
I have the following setup right now:
First Partition: Windows Xp
Second Partition: Ubuntu installed using Wubi (The partition was formatted as FAT32, and i installed ubuntu onto it using Wubi, due to a lack of a cd on hands).

Now i wanted to resize my windows parition to get more space on ubuntu from within ubunto, so i used gparted to attempt to resize my parition.
Problem is that i unmounted /dev/sda1 (windows partition) and now I am not sure how to mount it.

So i have two questions:
1) How do i remount the drive(still rather new to linux, sry....)? This doesn't seem to work like regular drive mounting works for some reason....mount -a doesn't do anything, adn rebooting still keeps the drive unmounted.
2) Can i resize my windows parition like this from ubuntu, becuase the resize/move button still doesn't work in gparted. Reason i have to do this from ubuntu is that my windows crashed, and i use it right now purely to store files :/.

Regards,

Thanks in advance.

---


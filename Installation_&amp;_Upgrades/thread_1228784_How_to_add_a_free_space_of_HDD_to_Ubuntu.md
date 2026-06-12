---
title: "How to add a free space of HDD to Ubuntu?"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by incrediblematt on 2009-08-01
Hello friends,

I really new to ubuntu, I tried to install ubuntu in my laptop, where i already had two operating systems. Windows XP and Windows7, i had some free spaces on my HDD so i tried to install ubuntu in those free spaces.
one free space was about 20GB and the other one was about 10 GB
while installing ubuntu i preferred the
"Guided-use the largest continous free space" option so ubuntu sucessfully installed in 20GB free space, now the remaining 10GB is still free. 
I just wanna add this 10GB free space to the installed ubuntu, so that i can make use of it.
I dont know how to add this free space. please help...

I thought if i format that free space to the ext3 file system then that free space would be recognizable by the ubuntu. but no luck. while i am trying to create a patition of that free space through the linux boot CD it is asking for mounting point. Really i dont know what to give there.. please help me to add that free space to my Ubuntu.

here is my partition structure

/dev/sda1 ntfs                  XP
/dev/sda7 ext3               Ubuntu
/dev/sda8 swap               ubuntu swap
/dev/sda5 ntfs                   local disk for windows
/dev/sda6 ntfs                  win7
free space                              now this should be added to ubuntu, how to do it?


Thanks in advance

---

### Post by x33a on 2009-08-01
format it to ntfs (if you want to access that space through windows too) or ext3.

then add entries to your /etc/fstab (mount settings) and you should be able to access that partition.

---

### Post by Bucky Ball on 2009-08-01
System->Administration->Partition Editor

Partition the free space in there. If you want to expand your Ubuntu partition to use the free space, you are going to need to do from the Live CD as the partitions have to be unmounted to work on. In your scenario now, you are okay because there is no partition to unmount, you are about to create one.

And yes, as mentioned, NTFS or FAT if you want to share with Windows.

:)

---


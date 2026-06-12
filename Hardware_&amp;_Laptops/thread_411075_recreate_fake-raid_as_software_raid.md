---
title: "recreate fake-raid as software raid?"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by mikedep333 on 2007-04-16
I recently deleted my jmicron software raid 0 array from its bios config (I would access the array using dmraid under linux), expecting to be able to recreate it from that utility and access it fine. After recreating it there, when I go to access it, the striping is off or something. I will open up a file detected in the raid array by a recovery utility, and parts of it will contain the data I want, while other parts of it will contain data from other files.

I would like to know if there is a way for me to recreate this raid array using mdadm or something in linux. I am looking for linux to detect how it is striped and put the stripes together. I know that the block size is 128KB, and I know that /dev/sda should presumably come before /dev/sdb.

I tried running: sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sd[ab] --chunk=128

but when I go to scan the md0 device, it seems like the data is corrupted (I may have messed up the MBR before, but when I go to scan for partitions using testdisk, the results are corrupt.

If anyone could help I would very much appreciate it. I have lots of valuable data on there that I haven't backed up in a while.

---

### Post by angryfirelord on 2007-09-03
Sounds like you nuked something. :) I'd grab a Knoppix CD, recover what you can from your partitions and simply do a re-install of Ubuntu with the proper RAID setup that you desire.

---


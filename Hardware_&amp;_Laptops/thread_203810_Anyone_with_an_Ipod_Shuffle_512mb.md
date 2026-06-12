---
title: "Anyone with an Ipod Shuffle 512mb?"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by Rob2687 on 2006-06-25
My shuffle is kinda messed up lately. Any of the machines I plug it into only read it as unknown USB device. I've tried the Apple Updater but the device isn't even recognized. Sometimes Ubuntu will detect it as a storage device though. From what I can tell the partitions on the shuffle are fubar....

Can anyone who has a shuffle do the following and email me the image? I will PM you my e-mail.

Run
```
dd if=/dev/sdX of=~/Desktop/shuffledump.bin
```
Where replace X with what ever your Ipod is. This will dump the firmware and the partition info to the bin file.

Thanks.

---

### Post by fdrake on 2006-07-01
I run the command and it created the shuffledump.bin file (517MB).

---


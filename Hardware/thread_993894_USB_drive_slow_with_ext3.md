---
title: "USB drive slow with ext3"
date: 2008-11-26
forum: Hardware
---

### Post by mschering on 2008-11-26
Hi, 

I just bought a new USB hard drive (USB 2.0, 7200rpm). Out of the box the drive was formatted FAT32. I did a speed test with hdparm:

sudo hdparm -t /dev/sdb1

/dev/sdb1:
 Timing buffered disk reads:  210 MB in  3.05 seconds =  68.75 MB/sec

Looks ok I thought. Then I formatted the drive with ext3 because I thought that's better when I use it with Linux only. After the format I ran hdparm again:

/dev/sdb1:
 Timing buffered disk reads:  102 MB in  3.01 seconds =  33.89 MB/sec


WOW it's half the speed it had with FAT32. Why is it so much slower with ext3?

Thanks for any help.

Best regards,

Merijn Schering

---

### Post by iggykoopa on 2008-11-26
it might be because the journaling. Have you tried it with ext2 instead? or maybe xfs(still has a journal but better performance IMHO)?

---

### Post by mschering on 2008-11-27
I will try ext2. But I just can't believe ext3 is so slow...

---

### Post by mschering on 2008-11-28
I think my first test results were false. Because when I reformat the drive with fat32 it also shows 33MB/s now. All filesystems show equal results now...

---


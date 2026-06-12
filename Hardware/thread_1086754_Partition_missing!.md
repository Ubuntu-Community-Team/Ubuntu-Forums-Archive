---
title: "Partition missing!"
date: 2009-03-04
forum: Hardware
---

### Post by Paulo_43505 on 2009-03-04
I have an Asus f53sv laptop with a 250GB Hard Drive.
I had Windows Vista installed and the hard drive was split in two partitions, one where Windows was installed and another just for data. 
I installed Ubuntu (dual boot with windows) in a new partition I created from the partition windows was installed. Everything was successful and both operating systems run fine. 
The problem is now I can't see the data partition; both operating systems say I have an 125GB Hard Drive!
Can anyone tell me how to recover my missing partition please?

PS- I tried some partition recovery software, only Test-disk could find the missing partition but I'm not sure how to use it.

Thanks in advance for all help you can provide

---

### Post by taurus on 2009-03-04
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---


---
title: "how to recover the lost partition??"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by harsha25 on 2009-09-05
while i was installing ubuntu i quit the installation as i thought to run it in parallel with windows vista,but now i can't find the 40GB(i gave 40GB for ubuntu) on the hard disk.

---

### Post by presence1960 on 2009-09-05
> **harsha25 said:**
> while i was installing ubuntu i quit the installation as i thought to run it in parallel with windows vista,but now i can't find the 40GB(i gave 40GB for ubuntu) on the hard disk.

Boot from the Ubuntu Live Cd and choose "try Ubuntu without any changes". When the desktop loads open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo fdisk -l
```
That is a lowercase L at the end. post the output back here.

---

### Post by shredder12 on 2009-09-05
you partition is not lost anywhere..
Many a times even after installing linux on a partition.. u are unable to see that partition in windows..
but using a partition manager in windows or thru the live cd you will be able to see the partition..

You may even try installing it again.. 
when you are asked to choose a partition, the cd's partition manager will show it to you...

---

### Post by harsha25 on 2009-09-05
Thanks for ur suggestions...i got it

---


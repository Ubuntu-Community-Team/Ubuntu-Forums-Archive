---
title: "Slow transfer rate of External Hard disk"
date: 2012-09-09
forum: Hardware
---

### Post by xProf on 2012-09-09
Okay, so I have an 140GB Toshiba External Hardisk with two partitions. Each has 70GB. 

It has been working well before where I can transfer files to and from my internal hard disk. But there's this one time where the other partition with 70GB became so slow when I transfer files from the external to internal. 

I have tried many ways on how to get it back but nothing happens. It has this loading stuff whenever I open that drive and I can't get the files inside that drive. But on the other partition, it is working well. I can transfer files at high speed but I cannot understand why is the other one is not working well. 

Is there any other complex ways to solve this? I really need to get those files because it is really important. 

Thanks,
- Juvar Abrera

---

### Post by 2F4U on 2012-09-09
It is not completely clear to me what the problem is. Can you read/write files but access is slow, or is it not possible to access the files. If you can't access the files the filesystem on that partition may be damaged or the disk itself has bad blocks. Did you check the SMART data in disk utility?

---

### Post by xProf on 2012-09-09
I can read the files but after a second, some sort of loading will appear and it will took like forever to finish the loading. I can't get files FROM the external hard disk and put files TO the external hard disk.

I can still access the files but the problem is the loading.

I do not know what SMART data in the disk utility is but it would be great if you tell me :D

Thanks.

---

### Post by LiamOS on 2012-09-09
What filesystem are you using? Could you post up the output of  fdisk -l  (or gdisk -l, if appropriate)? How is the drive connected to the computer?(USB, etc.)

---

### Post by xProf on 2012-09-10
It is connected through USB. 

I'm just going to say this again that it is working properly BEFORE.

---


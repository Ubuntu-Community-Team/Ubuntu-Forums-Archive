---
title: "Slow External Hard Drive"
date: 2017-08-30
forum: Hardware
---

### Post by chalatukas on 2017-08-30
Hello,

Few days ago I bought a 4TB Seagate external HDD. I what to use it as a backup drive. When I started coping files to that drive I noticed that it's really slow. Ubuntu disk benchmark test gives these results:

[IMG]http://i.imgur.com/rpCIw00.png[/IMG]

I have another external hard drive (Samsung 2TB) and did the same benchmark for it:

[IMG]http://i.imgur.com/4oluAgT.png[/IMG]

fdisk -l shows this information

```
Disk /dev/sdc: 3.7 TiB, 4000787029504 bytes, 7814037167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
**I/O size (minimum/optimal): 4096 bytes / 33553920 bytes**
Disklabel type: gpt
Disk identifier: E1A03E15-039D-40ED-B727-06844636DDC4

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.7T Microsoft basic data
```

I have feeling that the culprit is a "**I/O size (minimum/optimal): 4096 bytes / 33553920 bytes**" and tried to search for solutions to that on google but with no luck.

For the record I tried to create new partitions and/or format drive with gparted, parted, gdisk and even booted windows 10 and tried reformat using disk management. Furthermore, I tired EXT4 file system, but it not give any noticeable results.

Any suggestions or links appreciated.

---

### Post by TheFu on 2017-08-30
[https://www.backblaze.com/blog/hard-drive-failure-stats-q2-2017/](https://www.backblaze.com/blog/hard-drive-failure-stats-q2-2017/) was released yesterday.

I would return it for a refund ASAP.

---

### Post by chalatukas on 2017-08-30
> **TheFu said:**
> [https://www.backblaze.com/blog/hard-drive-failure-stats-q2-2017/](https://www.backblaze.com/blog/hard-drive-failure-stats-q2-2017/) was released yesterday.

I would return it for a refund ASAP.

Thank you for your reply. It lead me to a different path of Google searches than before. I was so focused on that I/O size that I didn't even questioned what type of specifications that drive have. Do be frank it never accured to me that newer hard drive can be made slower on purpose.

So I started searching about slow hard drives and found out that there is a new technology (Ok not that new. It's at least 4 years old) that is used to make hard drives. Hard drives made using it called [SMR hard drives]("http://www.tomsitpro.com/articles/shingled-magnetic-recoding-smr-101-basics,2-933.html").

[I think my hard drive is one of these hard drives.]("https://www.reddit.com/r/DataHoarder/comments/6m19zf/largest_shuckable_nonsmr_25_external/djz3vqc/") It's hard to tell because manufacturers do not advertise them openly. These hard drives had issues with write/read speeds from the beginning (especially small files!) and as far as I understand Linux (Kernel) do not support SMR hard drives fully. At least not yet.

So that in mind I booted to my windows 10 again and downloaded couple HDD benchmark programs to test my both external hard drives. [Here's the gallery of all the results]("http://imgur.com/a/kiTsu"), but short version is that in some test my new hard drive outperforms the old one and the difference in performance is not that great (1GB sample size for instance). Afterwards I tried benchmarks with the same sample sizes (50mb) on Ubuntu Gnome and speed where definitely lower.

In conclusion, I think that drive is working as design, because I could not replicate the same issues on Windows 10 and the problem lies with lack of support for SMR drives on Linux. Also I would like to mention that the last time I formatted the hard drive I did it on Windows 10 and I think It helped at least a bit. I still have one issue with this drive that I forgot to mention in OP is that it takes a long time to unmount after writing data on in, but I guess it is related with SMR.

So, I am marking this thread as solved (I just have to find out how to do it), but I would still appreciate any information or suggestions anyone can offer.

Writing down my hard drive's information to make find this thread easier:

Seagate Expansion Portable 4TB
STEA4000400
Model: ST4000LM024-2AN17V

Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt

---

### Post by jonee316 on 2017-12-14
I have a seagate backup plus 4tb and it is really slow on Ubuntu after filling it up with some files. Seems to be ok in Win 10 though. So I would think that we have the same case. 

I got 16.04 kernel 4.10.0-42-generic.

I will sell this then perhaps try wd.

---

### Post by janarbio on 2018-05-19
Hi, I also had similar problem with newly purchased Seagate 4TB. I reformatted the newdisk with Ubuntu's default 'Disk' program to partition and format. Then i had issues with copying data (> 2 hrs and hangs up), which  seemed very unusual. 
Then i installed '**gparted**' and then created **GPT partition table** via "Device-> Create partition table-> GPT". Then i created desired number of partitions with formats such as ntfs, ext4 etc... Now it works fine!

---

### Post by miltonlai on 2018-10-04
> **janarbio said:**
> Hi, I also had similar problem with newly purchased Seagate 4TB. I reformatted the newdisk with Ubuntu's default 'Disk' program to partition and format. Then i had issues with copying data (> 2 hrs and hangs up), which  seemed very unusual. 
Then i installed '**gparted**' and then created **GPT partition table** via "Device-> Create partition table-> GPT". Then i created desired number of partitions with formats such as ntfs, ext4 etc... Now it works fine!
I met the same issue and this solution really worked. Now in the disk benchmark the read/write is 66MBps / 20MBps, not that good but it is still much better than 1.5MBps.

---

### Post by zo1d on 2018-12-18
> **janarbio said:**
> Hi, I also had similar problem with newly purchased Seagate 4TB. I reformatted the newdisk with Ubuntu's default 'Disk' program to partition and format. Then i had issues with copying data (> 2 hrs and hangs up), which seemed very unusual. 
Then i installed '**gparted**' and then created **GPT partition table** via "Device-> Create partition table-> GPT". Then i created desired number of partitions with formats such as ntfs, ext4 etc... Now it works fine!

I wish I could give you beer, this has worked for me as well.

I recently bought a [COLOR=#000000]STEA4000400 and have spent 4-5 days trying to figure out what the hell was wrong with the drive. I tried a million things, so I did not really think this would work, but it did!

Thank you.[/COLOR]

---


---
title: "swap-ped partition recovery"
date: 2011-08-26
forum: Hardware
---

### Post by maspai on 2011-08-26
My harddisk partitions were Ext4 & FAT32. I installed ubuntu with "/" mount point in Ext4 partition, and accidentally selected the FAT32 one to be swap.

Now the files in that FAT32 partition (now, swap) can't be found. Can I recover them? It's never mind to delete the ubuntu, I will reinstall it :). Thanks for the help..

---

### Post by coffeecat on 2011-08-26
Since swap is barely a filesystem, it's possible that the FAT32 filesystem is undamaged.

First thing: whether you are running Ubuntu from the hard drive or from a live CD, run:

```
sudo swapoff -a
```

... from a terminal before you do anything else. You don't want anything written to that swap partition.

Have a look at this link:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

That describes how to recover a lost partition with testdisk (which is in the Ubuntu repository). That will only work if the FAT32 filesystem is undamaged. If you can't recover a viable filesystem, then use photorec which can recover a number of different filetypes. Both testdisk and photorec are described in that link. If you install testdisk, photorec comes with it.

I suggest you use a live CD and if you have to use photorec, make sure you have a large enough external USB drive to copy your rescued files to. It's best not to write files back to the drive you are rescuing from, even to a different partition.

---


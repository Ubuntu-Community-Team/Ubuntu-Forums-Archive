---
title: "Raid1 issues and question"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by upgrdman on 2005-05-12
I'm setting up a file server which has 4x IDE HDD's, and they will be used solely for 2 pairs of raid1 arrays, the only exception being a 15GB partition for "/".

I only have two ide channels, so a max of 4 devices could be used at once, so I had to unplug one of the HDD's and plug in my CD drive to install Ubuntu. This left with only being able to make the first raid1 array out of the first 2 HDD's.

Now I have unpluged the CD drive, and pluged in the fourth HDD. So now the question is just how do I make a raid1 array out of the 3rd and 4th HDD's... The ubuntu installer method was awesome...but I can no longer use CD's. Is there a tool similar to the one that came with the installer that I could now use?

Also, when I boot up, I get these errors:

> *adm: error opening /dev/md0: No such file or directory          [fail]
...
*Checking all file systems...
fsck.ext3: No such file or directory while trying to open /dev/md0
/dev/md0:
The superblock could not be read...

But then after I press Ctrl-D to continue boot-up as normal, it does realize (maybe it creates the md0 node?) my raid array during the "Mounting local filesystems..." stage, and everything works perfectly. I can access it and use it...

The only other error I get is something about a ror service unknown... not exactly sure because it scrolled by too quickly. Not sure if this is related to my above problems... but what is ror, and how do i fix it?

Thanks,
--Farrell F.

P.s. If it's not obvious, I'm new to Ubuntu/Debian in general... but not new to Linux. Ubuntu rocks...

---


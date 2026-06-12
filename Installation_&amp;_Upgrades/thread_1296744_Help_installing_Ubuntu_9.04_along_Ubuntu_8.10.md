---
title: "Help installing Ubuntu 9.04 along Ubuntu 8.10"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by mefateach on 2009-10-21
Hi
 
I want to install both os on one machine, having a dual-boot with grub. I have a single harddisk of 80G and 1G memory.
 
Could anyone instruct me how to make such an installation? In particularly, which partitions I should create during the installation, how not to override the second os, and how the grub's menu.lst should be configured.
 
Thanks!

---

### Post by tommcd on 2009-10-21
Just out of curiosity, why do you want to install both 9.04 and 8.10?

Anyway, here is how I would do it. I would install 9.04 first since it is the current stable version. (BTW, Karmic 9.10 will be out in just 8 days). When you get to the partitioning part of the install select manual partitioning and make these partitions:

/ (root) 10GB as ext3
swap 1GB
linux 10GB as ext3
/data the rest of the drive ext3. You will have to manually type in the mount point as /data. You could use /media/data, but I just use /data. The first 3 partitions can be primary partitions. Make /data a logical partition.

I suggest ext3 instead of ext4 since ext4 still has some issues in 8.10, and 9.04 too I think, but they are mostly fixed for 9.10.
Install 9.04 to the root partition and install grub to the MBR. Then install 8.10 to the "linux" partition. This partition will be mount point / (root) when you install 8.10. Mount the /data partition as /data when you install 8.10, and this time choose not to format /data since you already formatted it when you installed 9.04. Install the grub from 8.10 to the 8.10 root partition. You will have to select the "advanced" options to see this option.
 Both 9.04 and 8.10 can share swap and /data.
I recommend a separate /data partition instead of a separate /home partition so all the hidden config files and folders in home don't get mixed up between 8.10 and 9.04. This way there will be a /home directory on the root partitions of both 8.10 and 9.04. All your personal data can be stored in /data.
I boot several distros on my desktop and laptop and this is how I do it.
When you boot up 9.04, edit 9.04's /boot/grub/menu.lst and add this to the end of it to boot 8.10:
```

title Ubuntu 8.10
configfile (hd0,2)/boot/grub/menu.lst
savedefault

``` 
This assumes you make 8.10 root partition as the 3rd partition like I suggested above. This will chainload 9.04's grub into 8.10's grub so you can boot 8.10.
Here is a good tutorial on installing Ubuntu and using manual partitioning:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
And for the manual partitioning:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
The only difference is you will make a linux partition and a /data partition instead of a separate home.
Write back if you need more help.

And welcome to the Ubuntu forums!

---


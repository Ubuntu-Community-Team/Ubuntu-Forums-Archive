---
title: "Having trouble after clean install"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by dejansoftware on 2009-09-08
Hi,

I have installed latest Ubuntu Desktop Edition dual boot with windows XP.

1. Problem is when I try to install updates I get message that I don't have enough free space? Even a smallest update.

2. When I open Firefox, and enter web address, one second after that page opens, but the Firefox closes it down without any obvious reason.

Please help me to solve this.

Thanks

---

### Post by credobyte on 2009-09-08
Show us the output of:
```
df -h

```

---

### Post by dejansoftware on 2009-09-09
I don't know what you mean by code but I can sent you print screen of that

---

### Post by credobyte on 2009-09-09
> **dejansoftware said:**
> I don't know what you mean by code but I can sent you print screen of that

See attached screenshots ;)

---

### Post by drs305 on 2009-09-09
By code, he wants you to open a terminal (Applications, Accessories, Terminal) and type this:
```

df -Th

```

You will get something like this:
> /dev/sda1     ext4     15G  4.2G  9.9G  30% /

If you see 2.3 to 2.5G and close to 100% usage, keep reading.


There is a very good chance your install, if "side by side" with Windows, resulted in a / partition about 2.3-2.5 GB, which is not enough to support an Ubuntu installation. The default selection has been reported as a bug.

I've written some guides that can help:

If you have a 2.5 GB partition and want to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If you have a 2.5 GB partition and want to resize the partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Just in case you *do* have a normal partition size (10GB) and want to find out what is taking up so much space, refer to this guide:
[Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by dejansoftware on 2009-09-09
ok I have done it.:)

One more thing, Firefox works fine after I insert my USB disk, look's like it is all about hard disk space, right?
How can I resize it?

---

### Post by drs305 on 2009-09-09
Yes, it is drive space. You really don't have much choice if you want to run a normal Ubuntu installation except to reinstall it or move partitions around and take space from Windows. Your / system is only 2.5 GB. 

Here is a pic of Step 4 that must be changed, as explained in the link I provided previously.
[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874]("http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874")

---

### Post by dejansoftware on 2009-09-09
Ok, I will try to resize windows partition as you said, that means that I will not have to install system again Just to follow steps you mentioned. 
First Iwill put Ubuntu installation disk and do partition resizing, after that I will be able to use it normally?

---

### Post by drs305 on 2009-09-09
> **dejansoftware said:**
> Ok, I will try to resize windows partition as you said, that means that I will not have to install system again Just to follow steps you mentioned. 
First Iwill put Ubuntu installation disk and do partition resizing, after that I will be able to use it normally?

Yes. Just follow the guide. And be sure to back up important data before performing any repartitioning. You should defrag Windows first and also check your power source because resizing/moving partitions can take an hour or more, depending on the size being worked with.

---


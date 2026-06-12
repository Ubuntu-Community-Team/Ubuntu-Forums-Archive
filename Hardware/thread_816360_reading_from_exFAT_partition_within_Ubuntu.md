---
title: "reading from exFAT partition within Ubuntu"
date: 2008-06-02
forum: Hardware
---

### Post by Apoc112 on 2008-06-02
I searched around a bit, but didn't see this addressed anywhere.  I currently have quite a bit of data backed up on an external drive formatted to exFAT (stupidly...)

I no longer have a machine running Vista to access the data, so short of reinstalling Vista, is there any way to access this from Ubuntu? :(

Thanks for any help you can offer!

---

### Post by huwnet on 2008-06-02
I was wondering this myself not long ago and it seems there isn't yet an open source driver.

I guess you could install Vista in a virtual machine though.

---

### Post by Ux64 on 2008-09-25
So it seems that there aren't too much discussion about exFAT here either. exFAT seems to be pretty good file system after reading some facts about it.

[http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

Highlights:
[LIST]
[*]Free space allocation and delete performance improved due to introduction of a free space bitmap 
[*]Support for Transaction-Safe FAT File System (TFAT)
[/LIST]
Major disadvantage:
[LIST]
[*]Licensing status is unclear. However, Microsoft has previously patented portions of the FAT file system.[4] 
[/LIST]

I just got 1 TB external HDD and they tell that exFAT should be used with it... But I think I have to format it using "old" FAT32.

---

### Post by lrc3 on 2008-12-04
It's Microsoft new proprietary software, meaning we have to use our re-engineering skill to make it available on Linux/Ubuntu

---

### Post by cfabbriumd on 2009-02-08
Good NTFS support under Linux took a while to perfect. I remember a time where you had to partition your drive with a separate FAT32 partition to share files between OS's. Looks like support for exFAT will take just as long to develop, unless Microsoft releases the license. FAT chance that's going to happen.

---

### Post by frodowiz on 2013-02-27
i know its been a long time since this post so for others looking for a way using ubuntu 12.04 try this. (from other authors)
[http://blog.campodoro.org/?cat=10](http://blog.campodoro.org/?cat=10)

in a nutshell, running stock Ubuntu 12.04 it will auto-mount and you can create,format,change label and check exfat.

start with terminal:

```
sudo -s
apt-add-repository ppa:relan/exfat
apt-get install fuse-exfat exfat-utils
```you will be working  with FUSE since Linux wont have the  exfat guts in the kernel due to its proprietary nature. 

if anything different from stock 12.04 kernel you may have to install other things. refer to link. now format that 64 gig sd and enoy your big android phone downloads :)
 
thank you to the developer and to the blogger.

---


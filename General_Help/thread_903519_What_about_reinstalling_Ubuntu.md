---
title: "What about reinstalling Ubuntu?"
date: 2008-08-28
forum: General Help
---

### Post by Pidgin on 2008-08-28
When using Windows, it is much common to do a reinstallation. But in Ubuntu, we seldom hear about that. What should we do if the whole system comes into a chaos?
I just have no idea how to reinstall Ubuntu. There is only one partition. If we plan to format the partition, where do we backup our files?
Thank you!

---

### Post by Vivaldi Gloria on 2008-08-28
I think the best way is to shrink your ubuntu partition and create a new partition to save your files there. Now you can keep this new partition and reinstall ubuntu on top of the old ubuntu partition.

To shrink it you can boot the live ubuntu cd and use gparted (partition manager) which is available in the system menu.

---

### Post by VMC on 2008-08-28
> **Pidgin said:**
> When using Windows, it is much common to do a reinstallation. But in Ubuntu, we seldom hear about that. What should we do if the whole system comes into a chaos?
I just have no idea how to reinstall Ubuntu. There is only one partition. If we plan to format the partition, where do we backup our files?
Thank you!

When I installed ubuntu using the default install. It created one "root" partition and a "swap" partition. I like to keep things simple and only use the one partitions method.

If you open up a Terminal and type:

```
sudo fdisk -l
```

You will see the Linux partitions. You an use 'remastersys' to make an image of how ubuntu is currently setup including the installed applications. Since my "/home" is inside of the lone "root" "/" partition, I use a separate external program to backup my system. It's called Acronis True Image. I use it for a couple of reasons. One because it is blazingly fast. The other, is it's never failed to reinstall my system.

---

### Post by maybeway36 on 2008-08-28
One thing you could do is burn all of your files onto a DVD for backup.

---

### Post by anotherdisciple on 2008-08-28
Here is a nice page on making a seperate home partition.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Pidgin on 2008-08-29
> **anotherdisciple said:**
> Here is a nice page on making a seperate home partition.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

I think that is the best method. Have anyone tried it?

---

### Post by maybeway36 on 2008-08-29
I use a seperate home parititon on my hard drive. It comes in handy when you need to reinstall.

---

### Post by phoenix116 on 2008-08-29
i recently did that, it works really well, but I somehow messed up my file permissions and had to copy my home files from the backup

but now it works fine =D

---


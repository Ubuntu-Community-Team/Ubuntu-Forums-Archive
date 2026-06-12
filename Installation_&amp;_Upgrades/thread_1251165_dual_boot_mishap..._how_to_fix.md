---
title: "dual boot mishap... how to fix?"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by megamonk on 2009-08-27
i have 2 hard disk...

1 120gb hdd which is divided into 2 partitions. windows xp installed.
1 20gb hdd free.

im still a newbie at installing ubuntu so while installing i though that i was installing on the 20 gb hdd because it was the one i highlighted during install. installion was finished only to find out that the ubuntu installation was not on 20gb but on the first partition of the 120gb. what makes it even worst is that the filesystem is only 2gb in size and only has 155mb space left.

is there any way to move the ubuntu intallation to the 20gb hdd and use that hdd whole? i really dont know how to uninstall ubuntu from the 120 hdd without formatting it.

---

### Post by stlsaint on 2009-08-27
just to be sure...you have a 20gb hdd connected internally to the system? and thats what you want to put ubuntu on...but you installed it on another system over a windows(xp) install...now you want ubuntu gone? but without formatting it...i hope you didnt write ubuntu over xp but im confused on how you wrote to a [artition with xp on it? please give clarification if im wrong in  my assumptions!

---

### Post by megamonk on 2009-08-27
> **stlsaint said:**
> just to be sure...you have a 20gb hdd connected internally to the system? and thats what you want to put ubuntu on...but you installed it on another system over a windows(xp) install...now you want ubuntu gone? but without formatting it...i hope you didnt write ubuntu over xp but im confused on how you wrote to a [artition with xp on it? please give clarification if im wrong in  my assumptions!

i have 2 hdd.

a. 120gb with 2 partitions. windows is installed here.
b. 20gb empty. this is where i want to put ubuntu..

somehow during install (i dont know how coz im a newbie) i though i was installing ubuntu in my 20gb hdd because i highlighted (selected it) during install. but ubuntu got installed in the 120gb hdd where my windows is in. what makes it even worst is that ubuntu filesystem is only 2gb with 155mb free space. what i want to do is either

a. move my ubuntu installation from the 120gb hdd to the 20gb hdd then increase its file system to use the full 20gb or

b. uninstall ubuntu from the 120gb hdd window formatting it. i didnt use the wubi install so i dont know what to do.

i dont want to end up with 3 OS! where 2 os is in 120gb hdd and 1 os is in 20gb hdd

is it clear now? please help :confused:

---

### Post by fela on 2009-08-27
Do you mean that the 120GB HDD had 2 partitions, one for XP and one empty? If so it doesn't matter if you reformat the partition that was empty and reinstall ubuntu to the 20GB HDD (as there was no data on it). I think a good:

```
sudo fdisk -l
```

Is in order so I can see the layout of your partitions more in-depth. Please run this from either your ubuntu install or a livecd.

EDIT: you do know that if you installed ubuntu over a windows partition with data on it, your data will have been overwritten. Everything will be made clear with the fdisk -l though. Just post the output.

---


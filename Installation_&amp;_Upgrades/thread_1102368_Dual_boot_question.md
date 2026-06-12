---
title: "Dual boot question"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by barbolanero on 2009-03-21
So, this is the deal. I've just made a fresh install of windows XP and Ubuntu. On ubuntu everything is working just fine. But windows has a lot of issues, and I'd like to re-install it. I've read around that if I install windows I won't be able to boot linux again, and I don't want to install ubuntu again, since my PC is a little rebel and it took me a lot of work to get everything up and running. So, how can I install windows XP and then recover (or whatever) the grub?. I know for a fact that Gparted doesn't work on my pc (don't know why and have tried a lot of versions).

Just remembered. I have several partitions. 

HD1: 20 gb (XP), and another 20 gb
Hd2: 50 Gb (linux), 90 gb (home), and 20 gb (ntfs for music to be available from both systems)

---

### Post by tommcd on 2009-03-21
> **barbolanero said:**
> 
Just remembered. I have several partitions. 

HD1: 20 gb (XP), and another 20 gb
Hd2: 50 Gb (linux), 90 gb (home), and 20 gb (ntfs for music to be available from both systems)

So you have 2 hard drives then? I would assume that Windows XP is installed to the 1st primary partition of HD1, and Ubuntu is on HD2. Is that correct?
Post the output of:
```
sudo fdisk -l
```
so we can see your partition layout.
And please tell us:
what partitions Windows XP and Ubuntu are on
where is grub installed now? Is it on the master boot record of the 1st hard drive?
In any case, after you reinstall Windows the boot loader (grub) on the MBR will be overwritten and you will need to reinstall it. See this to reinstall grub from the live CD:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
And for everything you would ever want to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---


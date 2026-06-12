---
title: "dual boot installation"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by thick0 on 2005-12-27
Hi gang,

My laptop currently has an XP partition and a FC4 partition. I am planning to overwrite FC4 with ubuntu. Do I need to wipe the FC4 partition before installing ubuntu? Is there an ubuntu installation guide anywhere which discusses partitions?

Cheers

---

### Post by Koybe on 2005-12-27
If you want to get you /home back and if it's on a separate partion you don't need to wipe this one. Otherwise, juste erase the partitions and go for an install. It's quite easy just follow the steps. The only main difference is FC as a graphical install and ubuntu a text install (don't be afraid it's still with menus).

---

### Post by Herman on 2005-12-27
[https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")

That's the official one, (above).
Here's another good one, (Below).

[http://www.linuxnewbieguide.org/chap5.php]("http://www.linuxnewbieguide.org/chap5.php")

And then there are three slightly different installs in my signature link, (underneath).
 You can take a look at them all and then do it your own way if you want, or pick the one that suits you best.  :D (Herman)

---

### Post by thick0 on 2006-01-06
Hi Herman, top notch website, blimey, you must have spent some time on that.

I had a bit of a break for new year and now I am back again with more questions. First up, you created the 20gb FAT32 partition and then only used 10gb for ubuntu, any particular reason for leaving the other 10gb unused? Or am  I missing something?

Anyway, my situation. This is how my disk looks at the moment (sorry the formatting is crap):
[INDENT]
[tim@localhost ~]$ df -h
Filesystem            Size  Used Avail Use% Mounted on /dev/mapper/VolGroup00-LogVol00
                       18G  2.9G   15G  17% /
/dev/hda2              92M   14M   73M  16% /boot
/dev/shm              248M     0  248M   0% /dev/shm
/dev/hda1              37G   17G   20G  46% /mnt/windows
[tim@localhost ~]$[/INDENT]

The 18 gb is the FC4 partition. 92mb for boot, 248mb of swap space and the 37 gb is the windows partition. So far, so good.

So, I begin to install BB and get to the partitioning stage. I am presented with following partitions:

[INDENT]#1 primary 39.0 GB ntfs /media/hda1
#2 primary 98.7 mb ext3 /media/hda2
#3 primary 20.9 GB lvm[/INDENT]

I'm a bit confused by the different sizes but I guess:

#1 is the windows partition.
#2 is the the boot sector
#3 is the FC4 partition (with the swap space included?)

Now, if I allocate partition #3 as free space and then add room for a swap file, will ubuntu reuse the boot sector and drop the OS into partition #3? Or is the whole installation likely to go pear shaped.

I have never added a new linux OS on top of an old linux OS on a partitioned disk, I am running into a few problems.

Cheers

---


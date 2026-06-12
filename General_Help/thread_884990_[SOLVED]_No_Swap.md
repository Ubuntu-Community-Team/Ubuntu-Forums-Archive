---
title: "[SOLVED] No Swap"
date: 2008-08-09
forum: General Help
---

### Post by ShadowMKII on 2008-08-09
Hello,

I have a problem with having no swap when I start up Ubuntu.

At first, I had two swap partitions for the longest time (about the time when I first go Ubuntu - that was a year ago). About one week ago, I checked Gparted for reasons related to poor performance in GIMP. I discovered, on a tangent, that my two swap files were not in use, and only my small, 256MB swap file was. The other 4GB swap file was not being used at all, and I was stuck wondering why. I then deleted the old swap, activated the new one (the 4GB one via "Swap-on" in gparted) and then exited. Now, every time I start Ubuntu, there is no swap file in use at all. Can someone explain why? Do I have to make sure this is active at start up manually?

---

### Post by tamoneya on 2008-08-09
post the output of these commands:```
free -m
sudo fdisk -l
```
and the contents of this file:```
/etc/fstab
```

---

### Post by mannheim on 2008-08-09
Assuming these are actually swap **partitions**, I think you should check that you have corresponding entries in /etc/fstab. You should have something like:

```
/dev/sda3       none            swap    sw 0 0

```
(replacing /dev/sda3 by whatever your 4GB swap partition is.)

---

### Post by ShadowMKII on 2008-08-12
For tamoneya:

```
jordi@Shadow-Slate:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2013       1959         54          0         10        249
-/+ buffers/cache:       1699        313
Swap:            0          0          0
jordi@Shadow-Slate:~$ sudo fdisk -l
[sudo] password for jordi: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b396c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              34       10408    83337187+  83  Linux
/dev/sda3           10409       10892     3887730   82  Linux swap / Solaris
```


For both:

Here is the fstab file information:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=acbf7403-74a7-4b23-843f-f0eb04c05c15 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=118b646f-b3df-42f3-8e17-76f6e2d92b44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```


How does this look? Any further suggestions?

---

### Post by sdennie on 2008-08-12
Try:

```

sudo blkid

```

Note the UUID of the partition of type "swap".  Then:

```

gksudo gedit /etc/fstab

```

Find the line that defines swap and replace the long UUID string listed with the one from the blkid command.  Save the file and then try:

```

sudo swapon -a

```

---

### Post by ShadowMKII on 2008-08-13
Hello vor,

That appeared to work. Will this continue to work on start up? Also, did what you do replace the previous "swap" version with the new one that I made? Does it just allow the newer version that I made to be the default and active one?

Lastly, does swap only engage when most of the main memory is taken up?

Thank you very much for your help, along with everyone else.

---

### Post by sdennie on 2008-08-13
> **ShadowMKII said:**
> Hello vor,

That appeared to work. Will this continue to work on start up? Also, did what you do replace the previous "swap" version with the new one that I made? Does it just allow the newer version that I made to be the default and active one?


It should happen automatically at startup now and, yes the change just replaced whatever the system was previously looking for to make swap to what actually exists on your system now.  I forgot to mention that you should verify that everything looks ok with:

```

free -m

```

> 
Lastly, does swap only engage when most of the main memory is taken up?


More or less.  There is a kernel setting that decides at what point it should start moving less used memory to disk and it can be set so that it only moves memory to disk if it's completely out of RAM but, by default, it will start moving to disk much sooner than that and that's generally desired behavior.  This is a good post on the setting if you'd like to change it: [http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

---

### Post by ShadowMKII on 2008-08-17
Alright. Thank you for all of that information.

Consider this problem solved. ^^

---


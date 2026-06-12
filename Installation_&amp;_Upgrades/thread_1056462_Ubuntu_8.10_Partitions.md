---
title: "Ubuntu 8.10 Partitions"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by Salorian on 2009-01-31
Hello all, I have given up gaming...and I have no reason what so ever to continue to use Vista, so I am making a full Linux switch.

Here is my dilemma...

I have 2 250 GB Hard Drives, that I would like to use...

I have installed Ubuntu 8.10 64-bit in the following way.

/boot 5GB sda1 ext3
/swap 16gb sda5
/root the rest of my HD sda6 ext3

/home 250gb sdb1 ext3

Install went, fine and I am currently updating and playing with the package manager. However, I cannot access the other HD on /home. I cannot make a new folder, or even add any files to it.

My main goal is to install the OS and its needs on 1 HD, and use the rest for storage, and then use my other HD as storage as well.

How can this be achieved?

Thanks!

---

### Post by logos34 on 2009-01-31
post your 

cat /etc/fstab

and

sudo fdisk -l

---

### Post by Salorian on 2009-01-31
Small edit...I was wrong. I can access my /home, but I cannot access the root folder to use it as storage.

tom@tom-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d01bdc38-40f0-47ef-8705-387ccb767180 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=8ad0737d-4c32-4f2b-931c-061191bb9db6 /boot           ext3    relatime        0       2
# /dev/sdb1
UUID=0fe2ebd1-af84-40ec-84cc-4448a830dbc8 /home           ext3    relatime        0       2
# /dev/sda5
UUID=5896343d-f75b-447c-9c21-9b34dafafd04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


tom@tom-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcae74af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  83  Linux
/dev/sda2             609       30401   239312272+   5  Extended
/dev/sda5             609        2565    15719571   82  Linux swap / Solaris
/dev/sda6            2566       30401   223592638+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e7bbeda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

---

### Post by albinootje on 2009-01-31
> **Salorian said:**
> Small edit...I was wrong. I can access my /home, but I cannot access the root folder to use it as storage.

Can you explain this a bit more ?
/ is the root of the Linux filesystem tree, there's also /root which is the home of root, the sysadmin.

Are you saying you want a directory in / (but not in /home) to save data ?
You can do this :
```

sudo mkdir /data
sudo chown -R 1000:1000 /data

```
Then your default user should be able to read/write in /data

---

### Post by Salorian on 2009-01-31
Thanks for the replies!

When I installed, after my swap and /boot...I just used all the space left and put it under / (which I think means root)

So, I go into Places > Computer > Filesystem > root, its empty with 194.4GB free.

I basically want another place to store data aside from the /home.

I used the terminal commands you suggested, and I now have a folder called data with 194.4GB free, yet root says the same.

---

### Post by albinootje on 2009-01-31
> **Salorian said:**
> Thanks for the replies!

When I installed, after my swap and /boot...I just used all the space left and put it under / (which I think means root)

That is your / partition, which you can also call root partition I assume.
> 
So, I go into Places > Computer > Filesystem > root, its empty with 194.4GB free.

I basically want another place to store data aside from the /home.

I used the terminal commands you suggested, and I now have a folder called data with 194.4GB free, yet root says the same.

/data is part of the / partition. Try copying something to /data and see the difference.

---

### Post by Salorian on 2009-01-31
Okay....so the data folder we made is basically an extension of the root folder now, am I correct in saying that? So, I can just throw my junk in there, and use it as planned?

Also, is there anything illogical about my partitioning set up?

---

### Post by albinootje on 2009-01-31
And if you find it easier to have a link to /data on your desktop, try the following :

1) Open a terminal
2) Type in :
```

cd ~/Desktop ; ln -s /data

```
and press <enter>
Now you should have a link to /data on your desktop.

---

### Post by albinootje on 2009-01-31
> **Salorian said:**
> Okay....so the data folder we made is basically an extension of the root folder now, am I correct in saying that? So, I can just throw my junk in there, and use it as planned?

Yes, although it's better to talk about root partition (slash partition) because the root folder would be /root which is just the home folder of "root", the system administrator (you) of your machine.
> 
Also, is there anything illogical about my partitioning set up?
Looks excellent to me, it's cool and practical to have a separate /home partition.

---

### Post by Salorian on 2009-01-31
Thanks for all of your help, you were very helpful and I think I finally understand it! (it only took 5 installs)

Btw, Ultimate Boot CD is the best thing ever. =P

---

### Post by albinootje on 2009-01-31
> **Salorian said:**
> Thanks for all of your help, you were very helpful and I think I finally understand it! (it only took 5 installs)

Btw, Ultimate Boot CD is the best thing ever. =P

:)

Recommended reading :
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

### Post by Salorian on 2009-01-31
So, I re-did things a bit, lol.

Kept everything the same except...10gb for / and put home on my primary partition, then just formated the other HD with home/data and everything is great!

---

### Post by albinootje on 2009-01-31
> **Salorian said:**
> So, I re-did things a bit, lol.

You like reinstalling a lot ? :p
> 
Kept everything the same except...10gb for / and put home on my primary partition, then just formated the other HD with home/data and everything is great!
Excellent!

---


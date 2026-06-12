---
title: "New Hardy install, using the old /home partition"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by Egi_Power on 2009-09-30
I want to upgrade the hard disk in my laptop.
I was wondering if it's possible to do a clean install on the new disk and use the old /home folder, to keep the existing files.
I had Hardy on the old disk, and was thinking to use that on the new disk as well.

The old hard disk contains 3 partitions:

[I][FONT="Courier New"]/
/boot
/home[/FONT]
[/I]
On the new disk I plan to have just 2 partitions:
[I]
[FONT="Courier New"]/
/home[/FONT]
[/I]
Is there any way to do it?

Thanks in advance.

Egi_Power

---

### Post by presence1960 on 2009-09-30
> **Egi_Power said:**
> I want to upgrade the hard disk in my laptop.
I was wondering if it's possible to do a clean install on the new disk and use the old /home folder, to keep the existing files.
I had Hardy on the old disk, and was thinking to use that on the new disk as well.

The old hard disk contains 3 partitions:

[I][FONT="Courier New"]/
/boot
/home[/FONT]
[/I]
On the new disk I plan to have just 2 partitions:
[I]
[FONT="Courier New"]/
/home[/FONT]
[/I]
Is there any way to do it?


Thanks in advance.

Egi_Power

YES! You can use the old /home on the other disk.

Choose the manual install option. Highlight the /home partition and click Edit. Select filesystem from "use as", Set mount point to /home and **DO NOT TICK THE FORMAT BOX**. Set up your / and swap partitions the same way setting swap "use as" to linux-swap. / set "use as", tick the format box and set mount point to /

proceed with the install

P.S. if you use the old /home on the old disk as /home you won't be able to create /home on the new disk. You can only have one /home. But you can leave the old /home partition there on a new install but not set it to /home. it will be a storage/data partition and then you can create /home on the new disk. After the install you will have to mount the old /home partition and set permissions on it so you have read/write access,

---

### Post by mikewhatever on 2009-09-30
I think it's best to copy the old home to the new one before installing. This way the old home partition may serve for backup and storage.

---

### Post by Egi_Power on 2009-10-01
> **presence1960 said:**
> YES! You can use the old /home on the other disk.

Choose the manual install option. Highlight the /home partition and click Edit. Select filesystem from "use as", Set mount point to /home and **DO NOT TICK THE FORMAT BOX**. Set up your / and swap partitions the same way setting swap "use as" to linux-swap. / set "use as", tick the format box and set mount point to /

proceed with the install

P.S. if you use the old /home on the old disk as /home you won't be able to create /home on the new disk. You can only have one /home. But you can leave the old /home partition there on a new install but not set it to /home. it will be a storage/data partition and then you can create /home on the new disk. After the install you will have to mount the old /home partition and set permissions on it so you have read/write access,

Thank you for your reply.

I think I wasn't very specific about what I really want to do, so you didn't understand me fully.

Let's call my old 80 GB hard disk: disk old,
and my new 160 GB hard disk: disk new.

What I want to achieve is to move my old /home from disk old to disk new.

[FONT="Courier New"]
```

&#9556;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9559;           &#9556;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9559;
&#9553;  /home        &#9553;   move    &#9553;  /home        &#9553;
&#9553;  disk old     &#9553;  &#9552;&#9552;&#9552;&#9552;&#9552;&#9552;>  &#9553;  disk new     &#9553;
&#9562;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9565;           &#9562;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9565;

```
[/FONT]
The way you said it would just use my old disk's /home partition, but it wouldn't be moved to the new disk.



> **mikewhatever said:**
> I think it's best to copy the old home to the new one before installing. This way the old home partition may serve for backup and storage.

Thank you for your reply.

Exactly that is what I wish to do.
After a successful install I want to use the old disk for storage and backup purposes.

At the moment from the live CD I partitioned the new disk using GParted.
But I couldn't use GParted to copy the partition to the new disk.
First I unmounted the old /home partition.
Then I select copy [CTRL+C]
Then on the new disk I try to paste it to the future /home partition.
When I click on Apply I get an error message:

> GParted 0.3.5

Libparted 1.7.1

Copy /dev/sdb9 to /dev/sda4  00:01    ( ERROR )  
     calibrate /dev/sda4  00:01    ( SUCCES )  
     path: /dev/sda4
start: 41897520
end: 312576704
size: 270679185 (129.07 GiB)  
 
calibrate copy of /dev/sdb9  00:00    ( SUCCES )  
     path: /dev/sda4
start: 41897520
end: 312576704
size: 270679185 (129.07 GiB)  
 
calibrate /dev/sdb9  00:00    ( SUCCES )  
     path: /dev/sdb9
start: 117370953
end: 156296384
size: 38925432 (18.56 GiB)  
 
check filesystem on /dev/sdb9 for errors and (if possible) fix them  00:00    ( ERROR )  
     e2fsck -f -y -v /dev/sdb9  
     /dev/sdb9 is mounted.  
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Cannot continue, aborting.


 
 
 
 

========================================

/dev/sdb9 is the old /home partition on the old disk.
/dev/sda4 is the new /home partition on the new disk.
Any ideas?

Thanks in advance.

Egi_Power

---

### Post by presence1960 on 2009-10-01
you are right, I did not understand that you just wanted to move the data to the new /home. I thought you meant use the old /home. If gparted won't copy the partition you can install Ubuntu to the new disk and be sure you set sda4 as /home by highlighting it, clicking edit and setting parameters such as "Use as" -> choose filesystem & mount point choose /home. After the install you can mount the old /home and move all data to the new /home

P.S. here is a [link]("http://gparted.sourceforge.net/larry/move/move.htm") for copying using gparted.

---

### Post by Egi_Power on 2009-10-02
Thanks for the answer and the link.

I was looking in GParted, and find only one option which I could do something with.
It was *Set Disklabel*, of course.
I didn't have time to try anything that time, but somehow I had a feeling that this option has something to do with the solution.
Anyway, now I'm off to bed, but first thing in the morning is gonna be to try GParted again and Set Disklabel.

Cheers.

Egi_Power

---

### Post by Egi_Power on 2009-10-03
The *Set Disklabel* option in GParted wasn't the solution unfortunately.
:(

Any other idea how to copy my old /home partition to the new disk?

Cheers.

Egi_Power

---

### Post by presence1960 on 2009-10-03
> **Egi_Power said:**
> The *Set Disklabel* option in GParted wasn't the solution unfortunately.
:(

Any other idea how to copy my old /home partition to the new disk?

Cheers.

Egi_Power

I gave you as link with illustrated instructions in post #5 to do that.

---

### Post by fela on 2009-10-03
Couldn't you just do a clean install on the new drive without any mucking about, and then copy everything over from the old home folder to the new? This command would work, assuming you're booted on your new installation and the old disk is mounted at /media/disk:

```
sudo cp -rafv /media/disk/home/your_username/* /home/your_username/
```

Omit the v in -rafv if you don't want to see any messages. **[COLOR="Red"]CAUTION: you might want to backup your new settings just in case your old ones are broken. Just copy all the files and folders beginning with a . (period) from the new home folder to a separate folder on your hard drive.[/COLOR]**

---

### Post by Egi_Power on 2009-10-04
> **presence1960 said:**
> I gave you as link with illustrated instructions in post #5 to do that.

It wasn't clear that GParted has LiveCD.
So I used the Ubuntu LiveCD and tried to use GParted from there.

Anyway, after I downloaded the GParted LiveCD I used it to copy the partition.
The strange thing is that the old 5,9 GB home partition after the copy become 6,8 GB in size.
:-k

> **fela said:**
> Couldn't you just do a clean install on the new drive without any mucking about, and then copy everything over from the old home folder to the new? This command would work, assuming you're booted on your new installation and the old disk is mounted at /media/disk:

```
sudo cp -rafv /media/disk/home/your_username/* /home/your_username/
```

Omit the v in -rafv if you don't want to see any messages. **[COLOR="Red"]CAUTION: you might want to backup your new settings just in case your old ones are broken. Just copy all the files and folders beginning with a . (period) from the new home folder to a separate folder on your hard drive.[/COLOR]**

I guess I could do that, but there are 2 accounts on the old disk.
When I copy the old /home folder and its contents, I need a way to preserve the old permissions etc.

Egi_Power

---


---
title: "Formated a drive and now can't access it."
date: 2012-07-16
forum: Hardware
---

### Post by Peterfc on 2012-07-16
Hi

I have just used Gparted to format a spare hard drive so i can use it for data storage. When i try to drag a folder i get a message " The folder cannot be copied because you do not have permission to create it in the destination "

I have gone into Properties on the Data drive and in the Permission Tab " The permissions of and a load of numbers could not be determined "

Thanks for taking the time to read my Post

Peter

---

### Post by ahallubuntu on 2012-07-16
You probably do need to set permissions on the partition so your regular user can access it.

You can do this from a Nautilus folder I'm pretty sure - but I always do it from a terminal:

```
sudo chown -R YOURNAME:YOURGROUP /media/YOURPARTITION/*
```

(YOURNAME AND YOURGROUP may be the same, as Ubuntu makes a group for each user; for a single user they are probably the same, in a shared environment they wouldn't be the same.)

Once you (not root) owns the root of the partition, you may also need to set read/write privileges:

```
chmod -R 755 /media/YOURPARTITION/*
```

which gives you read-write on it and everyone else read and execute only.  If you're the only user, you could do 777 instead so any user could write to it as well, probably doesn't matter.  On some computers there are guest users so you may want to modify accordingly.

---

### Post by Peterfc on 2012-07-16
Hi

Thanks Ahallubuntu

I presume that Username and Yourgroup is the same but how do i find YOURPRITION name. 

I tried sudo chown -R peter:peter /media/peter/* and gt  a message. Cannot access /media/peter/* no such file or directory
peter@peter-dimension-2400:~$ 

Thanks for your patience in helping me Ubuntu is hard work at my age but i try before i ask for help. This is one i can't figure out. 

Peter

---

### Post by scradock on 2012-07-16
> **Peterfc said:**
> Hi

Thanks Ahallubuntu

I presume that Username and Yourgroup is the same but how do i find YOURPRITION name. 

I tried sudo chown -R peter:peter /media/peter/* and gt  a message. Cannot access /media/peter/* no such file or directory
peter@peter-dimension-2400:~$ 

Thanks for your patience in helping me Ubuntu is hard work at my age but i try before i ask for help. This is one i can't figure out. 

Peter

In a terminal type:

cd /media
ls -la

That will list the partitions that are mounted under /media in your Ubuntu install.

If you recognize one of the listed partitions as the one you want, use that in the instructions above.

If not, open Gparted and see if the new partition is mounted. If it is, it will have a key beside it in the list. The "mount point" will be listed as well - that's what you call it for the chown command.

If the new partition is NOT mounted, it will be identified only as "sdc1", if it's the only partition on the drive called sdc, for instance. Then you need to mount it before you can chown. Type:

sudo mount /dev/sdc1 /media/peter

for instance, if you want to call it peter.

Then you can go on with 

chown USR:USRGRP /media/peter

chmod 755 /media/peter

Hope that helps

---

### Post by sudodus on 2012-07-16
How did you format the partition in your spare hard drive? And how did you mount it?

Please post the output of the commands
```
sudo fdisk -lu
```
and
```
df
```

---


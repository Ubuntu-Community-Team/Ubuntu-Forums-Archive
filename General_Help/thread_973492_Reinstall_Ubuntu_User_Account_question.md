---
title: "Reinstall Ubuntu User Account question"
date: 2008-11-06
forum: General Help
---

### Post by javajeff1 on 2008-11-06
I have HOME mounted on a different partition(sdb5).  If I ever decide to reinstall(sdb1), what happens to my user account?  Do I choose the same username when Ubuntu asks and my login will automatically work?  The reason I am asking is because Windows can encrypt user data if that setting is checked.  I already know that I would do a manual install and choose my mounts / /home and swap.  I am just wondering how Ubuntu install knows I have a user account with settings.  Thanks!

---

### Post by taurus on 2008-11-06
If you mount that partition to /home and use the same username, then you can continue using the same $HOME.

---

### Post by javajeff1 on 2008-11-06
> **taurus said:**
> If you mount that partition to /home and use the same username, then you can continue using the same $HOME.

Thanks.  That was the whole reason I recently did a reinstall to separate the partitions.

---

### Post by brodiesel on 2008-11-06
hey jeff can you explain the process you did to repartition that? i'm looking at the same scenario.

---

### Post by mdurham on 2008-11-06
Not sure if this is any use, but what I do is:
login as root
move my home to a different partition
create a link to the home that's now on the new partition
copy the link to where home was removed from originally
remove (rename) 'link to' from the link name
login as user
finished

no need to mess about with fstab.

---

### Post by javajeff1 on 2008-11-07
I originally tried moving home, but I had login problems so I did a reinstall.  The Ubuntu gives you three options I believe when it comes to partitioning, and I chose "Manual."  I am using a second hard drive (250gb), and had it create three partitions.  I created the first ext3, then chose mount /.  Then I created the second, and chose /home.  While I was creating them, I did the math in my head to save 6GB for the last one, which is swap.  I do not know if 6GB is too big or not, but I guess I can always change it later and currently have plenty of space.  Ubuntu took it from there and continued along the install.  I have always found 3 partitions like this setup to be very good from old school Red Hat/Mandrake days.

---

### Post by brodiesel on 2008-11-07
Thanks, I think I'm going to go this route. 

Two remaining questions:

If I create a copy of /home right now on my external hd, can i insert that into a future installed version? 

Second, how does one go about "wiping" everything thats currently on the Ubuntu partition that I'm going to reinstall? (I have a dual boot Ubuntu/XP setup). Is this just a part of the partitioning in the original installation? Its been a while since I've done a clean install...

---

### Post by javajeff1 on 2008-11-07
You want to mount your new home, then try the following to see if it copies everything.

$cd /home/
$sudo find . -depth -print0 | sudo cpio –null –sparse -pvd /mnt/newhome/

Here is a resource:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Make sure you add sudo in your command, because it did not work when I tried to follow the instructions.

---


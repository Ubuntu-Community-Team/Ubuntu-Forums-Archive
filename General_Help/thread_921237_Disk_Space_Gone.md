---
title: "Disk Space Gone"
date: 2008-09-16
forum: General Help
---

### Post by TheTurk on 2008-09-16
I'm fairly new to Ubuntu, so treat me with kid gloves ;)

I've got a very weird problem where all of my disk space is constantly being consumed. But I can't track down where this is being used.

I have only about 30GB of legitimately used space on a 150GB drive. Ubuntu reports that I have 100% of the drive space used. I can verify that this is the case by using Partition Editor. But if I run the Disk Usage Analyzer, it reports that I've only used about 30GB (which is about right).

I know that I did have Simple Backup doing backups on a regular basis that filled up this drive at one point. I've turned this off, deleted the backups, emptied the trash, etc. After doing this, I had the appropriate amount of space left.

Since then, the drive still continues to fill up. Even if Simple Backup is still running, it's not creating back-ups in the location specified. Nothing is showing up in Disk Usage Analyzer. I've run a number of terminal based commands with no luck tracking down this used space.

It's almost as though hidden files are being created and I just can't see them.

Any ideas? Thanks!

---

### Post by iaculallad on 2008-09-16
Had you tried cleaning your repository update/download cached files?

```
sudo apt-get clean
suso apt-get autoremove
```

Also, try cleaning your /boot filesystem folder.

```
sudo rm /boot/*.bak
```

---

### Post by TheTurk on 2008-09-16
I just tried those commands and they had very little affect.

If it helps, here's screenshots of the results. Note that the server directory is actually another mounted drive.

---

### Post by iaculallad on 2008-09-16
What about **df -h**, what does it display?

```
df -h
```

---

### Post by TheTurk on 2008-09-16
Here are the results:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             143G  119G   17G  88% /
varrun                2.0G  324K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   48K  2.0G   1% /dev
devshm                2.0G   12K  2.0G   1% /dev/shm
lrm                   2.0G   44M  1.9G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1             688G  454G  199G  70% /server
gvfs-fuse-daemon      143G  119G   17G  88% /home/travisp/.gvfs

---

### Post by iaculallad on 2008-09-16
> **TheTurk said:**
> Here are the results:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             143G  119G   17G  88% /
varrun                2.0G  324K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   48K  2.0G   1% /dev
devshm                2.0G   12K  2.0G   1% /dev/shm
lrm                   2.0G   44M  1.9G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1             688G  454G  199G  70% /server
gvfs-fuse-daemon      143G  119G   17G  88% /home/travisp/.gvfs

It seems that you still have 88% of free disk space in your root (/) filesystem folder. I still prefer using the **df** command when checking on my free spaces since the Disk Usage Analyzer utility does not show the correct disk space usage. You're system is in good shape.

---

### Post by TheTurk on 2008-09-16
Actually, it says that I only have 17 GB of free space. And that's only because I went through and deleted a ~17GB video. Before that, I was pegged at 100% usage and couldn't do anything.

---

### Post by prshah on 2008-09-16
> **TheTurk said:**
> Actually, it says that I only have 17 GB of free space. And that's only because I went through and deleted a ~17GB video. Before that, I was pegged at 100% usage and couldn't do anything.

If you have _lots_ of tiny files, you could have run out of inodes; check with ```
df -i
```

---

### Post by TheTurk on 2008-09-16
This is the results of that command. Looks pretty normal.

```
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1            9396224  209797 9186427    3% /
varrun                506821      75  506746    1% /var/run
varlock               506821       1  506820    1% /var/lock
udev                  506821    2934  503887    1% /dev
devshm                506821       2  506819    1% /dev/shm
lrm                   506821      14  506807    1% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1            91586560  161571 91424989    1% /server
gvfs-fuse-daemon     9396224  209797 9186427    3% /home/travisp/.gvfs

```

---

### Post by tuxxy on 2008-09-16
You say you emptied your users trash but maybe not all the trash?

i know the root trash can be a problem on occasions

Open a terminal and type

```
sudo find / -type d -iname *Trash* | grep Trash

```

You should now have a list of trash folders, you can use nautilus now if you want to check the contents, for example to view the roots trash you could type this

```
gksu nautilus /root/.local/share/Trash

```

---

### Post by Burillo on 2008-09-16
did anyone of you think of root? i had this problem once, ext3 consumed ~70GB on a freshly formatted drive. ext3 got this thing, called reserved space. if you hard drive is filled up - you logon as root and do maintenance (btw Ubuntu has no root by default so you end up pretty much f**cked if you haven't set up root password). this is useless on external drives, but this DOES actually make sense on a system partition, so you better leave things as they are now. but if you absolutely want to - you can execute this:
```
tune2fs -m PERCENTAGE_OF_RESERVED_SPACE DRIVENAME
```
so if you want ext3 to reserve say 5% on /dev/sda1 you type:
```
tune2fs -m 5 /dev/sda1 
```
this should help

---

### Post by Burillo on 2008-09-16
deleted

---

### Post by prshah on 2008-09-16
> **Burillo said:**
> 
 ext3 got this thing, called reserved space. if you hard drive is filled up - you logon as root and do maintenance (btw Ubuntu has no root by default so you end up pretty much f**cked if you haven't set up root password). 


Actually, the reservation of space is a linux thing, not ext3- related; it does so even on an ext2 / reiserfs partition.

And Ubuntu _does_ allow root logins; just not _graphical_ root logins. (Actually, it can do that as well, it's just a big no-no, and that makes sense).

Recovery mode is an example of a root login, though you can have a root login in regular mode as well.

---

### Post by Burillo on 2008-09-16
ubuntu is linux, every linux is capable of that. i just wanted to note that it's not that easy for a newbie to get to root.

---

### Post by TheTurk on 2008-09-17
OK, problem solved.

It appears that a couple of the backups I deleted (from my backups gone wild experience) ended up in /root/.local/share/Trash/files directory. I had to delete these as root user.

I guess I don't understand how the trash system works in unix. How does it determine whether to use a user's trash or the root trash. I'm assuming it all depends on the user the process is running as that asks to delete a file/directory. 

When does Ubuntu decide to clean the trash? In my case, that was never being done (at least correctly).

Thanks again for all the help!

---

### Post by mb_webguy on 2008-09-17
> **TheTurk said:**
> OK, problem solved.

It appears that a couple of the backups I deleted (from my backups gone wild experience) ended up in /root/.local/share/Trash/files directory. I had to delete these as root user.

I guess I don't understand how the trash system works in unix. How does it determine whether to use a user's trash or the root trash. I'm assuming it all depends on the user the process is running as that asks to delete a file/directory. 

When does Ubuntu decide to clean the trash? In my case, that was never being done (at least correctly).

Thanks again for all the help!

A file goes into the Trash of the user that deleted it.  Almost all of the time, that will be your user account (or the other regular user accounts, if more than one person has an account on the computer).  However, if you run Nautilus as root, such as by entering the command "gksu nautilus", then if you delete something it will go into root's Trash.

Also, be aware that there is no trash for the command line.  If you delete a file in the terminal using the "rm" command, it's completely gone.

And as far as I know, you have to manually empty the Trash.

---

### Post by balserodeluxe on 2008-10-04
I have a similar problem but cannot find the files. Actually I found them at first and deleted them manually using the rm command found in some of the replies to this forum. This is the output of df:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1             76966596  64245844   8841860  88% /
varrun                  485048       260    484788   1% /var/run
varlock                 485048         0    485048   0% /var/lock
udev                    485048        64    484984   1% /dev
devshm                  485048         0    485048   0% /dev/shm
lrm                     485048     39760    445288   9% /lib/modules/2.6.24-19-generic/volatile
/dev/md1             484535440 200853092 259263152  44% /raid
gvfs-fuse-daemon      76966596  64245844   8841860  88% /home/mythbuntu/.gvfs

I have two disks, the one running out of space is sdc1 and gvfs-fuse-daemon indicates 88%...

df -i returns this:

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sdc1            4849664  180749 4668915    4% /
varrun                121262      78  121184    1% /var/run
varlock               121262       2  121260    1% /var/lock
udev                  121262    3088  118174    3% /dev
devshm                121262       1  121261    1% /dev/shm
lrm                   121262      19  121243    1% /lib/modules/2.6.24-19-generic/volatile
/dev/md1             30531584  149051 30382533    1% /raid
gvfs-fuse-daemon     4849664  180749 4668915    4% /home/mythbuntu/.gvfs

---

### Post by Ape3000 on 2008-10-04
I like to use the following command to hunt down the disk space eaters:
> sudo du -x --block-size=1024K | sort -nr | head -10

---


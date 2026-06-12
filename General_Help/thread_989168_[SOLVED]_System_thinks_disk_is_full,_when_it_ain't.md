---
title: "[SOLVED] System thinks disk is full, when it ain't"
date: 2008-11-21
forum: General Help
---

### Post by Paqman on 2008-11-21
My system has just gone crazy, and thinks the disk is full, even though it isn't.

I'm running Intrepid with a 19GB root partition, of which a little over 9.7GB is used. However, somehow the system seems to have got the idea that the disk is full, and therefore won't let me download anything.

I've rebooted to clear /tmp and really can't see why it would be miscalculating the free space. Any ideas?

Check it out:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9              18G   17G     0 100% /
tmpfs                 996M     0  996M   0% /lib/init/rw
varrun                996M  220K  996M   1% /var/run
varlock               996M     0  996M   0% /var/lock
udev                  996M  2.8M  993M   1% /dev
tmpfs                 996M  524K  996M   1% /dev/shm
lrm                   996M  2.4M  994M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda8              38G   23G   14G  63% /home
overflow              1.0M   20K 1004K   2% /tmp

```

---

### Post by drs305 on 2008-11-21
You can check your trash to see if there are deleted files which still are taking up space. The link in my signature line details the ways to find and delete these files. It also has other tips on cleaning up your system files to regain space.
Here's the link:

[Disk Full - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

To check your root trash folder  (shift-del to delete these files):
```

gksudo nautilus /root/.local/share/Trash/files

```

---

### Post by eldragon on 2008-11-21
there is a 5% of space from every ex2/3 partition that is reserved for the root account. this is due to the fact that certain daemons require to be able to write to the disk in case you fill the partition.

i wouldnt modify /'s since all these daemons write there anyway.

but you can recover your /home's partition reserved space by:

create a root's accound password:
```

$ sudo passwd root

```

log out of your account, hit ctrl-alt-f1 to go to a text terminal.

log with your root account.
first
```

# cat /etc/mtab

```
locate the name of the home partition, for example:
```

/dev/sda1 /home ext3 rw 0 0

```
the name is /dev/sda1

then do
```

# /etc/init.d/gdm stop
# umount /home
# tune2fs -m 0 /dev/sda1
# mount /home
# /etc/init.d/gdm start

```

first command: stop xorg.
second comand: umounts /home (make sure there is no error here)
third command: tells the fs that it has to reserve 0% of partition size for root user, remember to replace /dev/sda1 with your own.
fourth command: mount home agan
fifth command: restart xorg.

again; DO NOT DO THIS WITH THE / PARTITION. 

good luck

---

### Post by Paqman on 2008-11-21
> **drs305 said:**
> You can check your trash

Been there, done that (for both user and root). Im really scratching my head on this. I was doing a large backup using rsync from my NAS to a USB drive and at the end of it my drive thinks it's full. Even though i've not moved any data onto it.

Some oddities: (sda7 & sda8 being root and home respectively)

---

### Post by sancho panza on 2008-11-21
> **Paqman said:**
> My system has just gone crazy, and thinks the disk is full, even though it isn't.

I'm running Intrepid with a 19GB root partition, of which a little over 9.7GB is used. However, somehow the system seems to have got the idea that the disk is full, and therefore won't let me download anything.

I've rebooted to clear /tmp and really can't see why it would be miscalculating the free space. Any ideas?

Check it out:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9              18G   17G     0 100% /
tmpfs                 996M     0  996M   0% /lib/init/rw
varrun                996M  220K  996M   1% /var/run
varlock               996M     0  996M   0% /var/lock
udev                  996M  2.8M  993M   1% /dev
tmpfs                 996M  524K  996M   1% /dev/shm
lrm                   996M  2.4M  994M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda8              38G   23G   14G  63% /home
overflow              1.0M   20K 1004K   2% /tmp

```

Clearly, your root partition has 100% usage. I think this is probably the[ bug discussed here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285"), wherein the system log processes write to /var/log folder and flood the log files to take up the entire root partition. To fix the problem, go thru [this comment]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285/comments/52") on the bug report. 
A temporary fix would involve locating the bloated files in /var/log and deleting them before rebooting.

Cheers!

---

### Post by Paqman on 2008-11-21
> **sancho panza said:**
> 
A temporary fix would involve locating the bloated files in /var/log and deleting them before rebooting.


That was one of the first places I looked. There's only 9.5MB in /var/log.

---

### Post by philinux on 2008-11-21
Install kdirstat and have a good look at root. There's no menu item created but it gives a really good display of file structures and sizes.

---

### Post by Paqman on 2008-11-21
> **philinux said:**
> Install kdirstat and have a good look at root. 

Similar story to what I got out of Baobab. No clue as to why a 19GB partition would think it was full:

---

### Post by philinux on 2008-11-21
There must be some hidden files in there or something.

---

### Post by sancho panza on 2008-11-21
> **Paqman said:**
> Been there, done that (for both user and root). Im really scratching my head on this. I was doing a large backup using rsync from my NAS to a USB drive and at the end of it my drive thinks it's full. Even though i've not moved any data onto it.

Some oddities: (sda7 & sda8 being root and home respectively)

This is confusing. The system (both df tool and Gparted) says that sda9 is root and it is almost full. You are correct that sda7 is with 9.7GB used, but that is not the root! Try digging deeper into all folders mounted on root using kdirstat of baobab.

---

### Post by prshah on 2008-11-21
> **Paqman said:**
> My system has just gone crazy, and thinks the disk is full, even though it isn't.


Check if you've run out of inodes;```
df -i
```

Can happen if you have lots of tiny files.

---

### Post by Paqman on 2008-11-21
> **sancho panza said:**
> This is confusing. The system (both df tool and Gparted) says that sda9 is root and it is almost full. You are correct that sda7 is with 9.7GB used, but that is not the root! Try digging deeper into all folders mounted on root using kdirstat of baobab.

My mistake, sda8 & 9.

Really can't see where all this extra cruft is hiding...

---

### Post by Paqman on 2008-11-21
> **prshah said:**
> Check if you've run out of inodes;```
df -i
```

Can happen if you have lots of tiny files.

andy@intrepid-desktop:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda9            1144640  140655 1003985   13% /
tmpfs                 254871       3  254868    1% /lib/init/rw
varrun                254871      67  254804    1% /var/run
varlock               254871       2  254869    1% /var/lock
udev                  254871    5199  249672    3% /dev
tmpfs                 254871       2  254869    1% /dev/shm
lrm                   254871      17  254854    1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda8            4964352   61352 4903000    2% /home
overflow              254871      63  254808    1% /tmp

---

### Post by psusi on 2008-11-21
> **Paqman said:**
> 
I'm running Intrepid with a 19GB root partition, of which a little over 9.7GB is used.

What makes you think only 9.7 GB is used?  Because the df you posted says it's all used.

> **eldragon said:**
> there is a 5% of space from every ex2/3 partition that is reserved for the root account. this is due to the fact that certain daemons require to be able to write to the disk in case you fill the partition.

His problem is that he thinks the disk should only be HALF used, not 95% used and is wondering where the other 5% is.

> **eldragon said:**
> 
create a root's accound password:
```

$ sudo passwd root

```

log out of your account, hit ctrl-alt-f1 to go to a text terminal.

log with your root account.
[/code]

No, no no, do NOT mess with the root password.  And there is no need to use a text terminal; just use sudo in a normal terminal window.  If you want to run the next several commands as root without having to retype sudo each type, then just run sudo -s first, and then exit when you're done.

> **eldragon said:**
> ```

# /etc/init.d/gdm stop
# umount /home
# tune2fs -m 0 /dev/sda1
# mount /home
# /etc/init.d/gdm start

```

Best just to use tune2fs from the livecd so you don't have to mess with shutting down gdm, and hoping that nothing else is using files on /home, and you can do this to your root as well.

Paqman: Your filesystem might be slightly corrupted.  Boot from the livecd and fsck -f /dev/sda6 and see if it finds and fixes any errors.

---

### Post by Paqman on 2008-11-21
> **psusi said:**
> What makes you think only 9.7 GB is used?  Because the df you posted says it's all used.


Because that's how full it was a couple of hours ago. I've not moved any data onto it. Baobab backs this figure up.

The way I see it there's three possibilities:

[LIST=1]
[*]The disk is full. Somehow a large amount of junk data has been written to it, which is somehow hidden from view.
[*]The disk is not full. The system is calculating disk usage wrongly.
[*]The disk has shrunk.
[/LIST]

---

### Post by Paqman on 2008-11-21
> **psusi said:**
> 
Paqman: Your filesystem might be slightly corrupted.  Boot from the livecd and fsck -f /dev/sda6 and see if it finds and fixes any errors.

Rats, I thought this might be it, but no luck. According to fsck, all is well with the partition.

---

### Post by unutbu on 2008-11-21
Paqman, are you running baobab as root (gksu baobab)?
When you run baobab as a normal user, the numbers it reports do not include the size of any file that is not readable as that user. 

So if baobab and df are reporting very different numbers, it is likely that the files that are taking up space are owned by root and/or unreadable by the normal user account.

---

### Post by happyhamster on 2008-11-21
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=677185&page=3](http://ubuntuforums.org/showthread.php?t=677185&page=3)

---

### Post by Paqman on 2008-11-21
> **unutbu said:**
> Paqman, are you running baobab as root (gksu baobab)?
When you run baobab as a normal user, the numbers it reports do not include the size of any file that is not readable as that user. 

So if baobab and df are reporting very different numbers, it is likely that the files that are taking up space are owned by root and/or unreadable by the normal user account.

D'oh! I wasn't, no.

And lo and behold, when running it as root, it showed up a 12GB backup file that sbackup had written to a folder in /media that is used as a mountpoint for my NAS.

Mystery solved, and I am suitably red-faced for overlooking something that basic!

---


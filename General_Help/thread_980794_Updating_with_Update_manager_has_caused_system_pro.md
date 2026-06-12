---
title: "Updating with Update manager has caused system problems - how to resolve or reverse."
date: 2008-11-13
forum: General Help
---

### Post by Thaismai on 2008-11-13
Hi there, 

My first post!

I've been playing around with the new Ubuntu release on a USB install. I'm using a sandisk Titanium 2GB for this. I've installed twice now and ran into the same problem both times. 

Using the Update manager to install updates, I eventually run into this error message:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I run dpkg --configure -a in the terminal, but it says I need superuser privelege. 

After hunting around I find a post with a similar problem, and use:

dpkg --configure -a

which is met with the following response:

> ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0145' near line 1:
 newline in field name `#padding'

so then I try 'sudo apt-get update'

which works and comes up with:

> Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US and so on...

That's ok until it comes up with:

...... > W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ubuntu@ubuntu:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
 - same problem as before, and there's definitely enough space on the device. 

Also, my Firefox bookmarks have dispeared, and I'm unable to load Pidgin. Last time I installed it, it did the same thing, I eventually stopped working so I had to go back into windows, format and re-install. 

I could use the package manager to install programs before starting the update, and I was able to install some of the update files, but now its ceased to work. 

Any ideas on how to resolve or roll-back updates?

Thanks, 
James.

---

### Post by geirha on 2008-11-13
What's the output of df? ```
df -h
```

---

### Post by Thaismai on 2008-11-13
Hi Geirha,

> ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 981M  2.0M  979M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 981M  2.0M  979M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 981M     0  981M   0% /lib/init/rw
varrun                981M  112K  981M   1% /var/run
varlock               981M     0  981M   0% /var/lock
udev                  981M  2.8M  978M   1% /dev
tmpfs                 981M  864K  980M   1% /dev/shm
rootfs                788M  788M     0 100% /
/dev/sdb1             2.0G  1.5G  449M  77% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 981M   28K  981M   1% /tmp
/dev/scd1             6.4M  6.4M     0 100% /media/U3 System
/dev/scd2             6.7M  6.7M     0 100% /media/U3 System_
/dev/sdc              7.5G  4.6G  3.0G  61% /media/CRUZER8

---

### Post by Thaismai on 2008-11-13
easier to read:

[HTML]ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 981M  2.0M  979M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 981M  2.0M  979M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 981M     0  981M   0% /lib/init/rw
varrun                981M  112K  981M   1% /var/run
varlock               981M     0  981M   0% /var/lock
udev                  981M  2.8M  978M   1% /dev
tmpfs                 981M  864K  980M   1% /dev/shm
rootfs                788M  788M     0 100% /
/dev/sdb1             2.0G  1.5G  449M  77% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 981M   28K  981M   1% /tmp
/dev/scd1             6.4M  6.4M     0 100% /media/U3 System
/dev/scd2             6.7M  6.7M     0 100% /media/U3 System_
/dev/sdc              7.5G  4.6G  3.0G  61% /media/CRUZER8[/HTML]

---

### Post by geirha on 2008-11-13
```
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
...
rootfs                788M  788M     0 100% /

```

It really is full ...

---

### Post by Thaismai on 2008-11-13
But how has it filled the entire partition I created on the USB for it?  If it has filled up the extra space i left it it has done so in error, the 30mb or so of updates its installed so far can't possibly fill the space, and does this explain the nature of the error?

After reboot problem persists.

---

### Post by Thaismai on 2008-11-13
If there is a corrupted file or something taking up so much space, I should be able to find it and move it somewhere else. 

This is a long shot, but the following folders seem to have a lot of crap in them:

proc 896.2 MB (some contents unreadable)
rofs 1.7 GB (some contents unreadable)
Sys 576.1 MB (some contents unreadable)
Var 321.4 MB (some contents unreadable)

What could this stuff be?

---

### Post by geirha on 2008-11-13
When you install packages, it stores them in /var/cache/apt/archives/ and they don't get deleted after the package is install. You can clean up with ```
sudo apt-get clean
```

Not sure why /proc and /sys are showing that much space. But try this command:```
sudo du -h -x --max-depth=1 /
``` to see where the space on the filesystem / is on is located (that is, the -x option will make it not check other filesystems)

---

### Post by Thaismai on 2008-11-13
ran 'sudo apt-get clean', var now showing 209.9 MB.

```
ubuntu@ubuntu:~$ sudo du -h -x --max-depth=1 /
7.9M	/etc
4.0K	/cdrom
1.7G	/usr
215M	/var
106M	/lib
75K	/root
8.7M	/sbin
16K	/lost+found
0	/tmp
0	/rofs
26K	/media
5.9M	/bin
du: cannot access `/home/ubuntu/.gvfs': Permission denied
100M	/home
1.7M	/boot
0	/dev
0	/mnt
0	/opt
0	/proc
0	/srv
0	/sys
2.1G	/
```

I don't know if this helps, but I checked out the stuff in rofs as that's where the loop file is located yes? 

rofs/usr/lib 650.8 MB
rofs/usr/share 692.2 MB 
is this normal?

When I enter 'sudo dpkg --configure -a'

I get:
'parse error, in file `/var/lib/dpkg/updates/0145' near line 1:
 newline in field name `#padding''

Could this have anything to do with anything?

---

### Post by geirha on 2008-11-13
> **Thaismai said:**
> 

I don't know if this helps, but I checked out the stuff in rofs as that's where the loop file is located yes? 

rofs/usr/lib 650.8 MB
rofs/usr/share 692.2 MB 
is this normal?


I don't know really, I don't have any experience with such an install

> **Thaismai said:**
> 
When I enter 'sudo dpkg --configure -a'

I get:
'parse error, in file `/var/lib/dpkg/updates/0145' near line 1:
 newline in field name `#padding''

Could this have anything to do with anything?

My best guess is that dpkg attempted to write something to that file, but since there were no space left, it didn't manage to finish. I found this thread which seems to be the same problem. Has an apparent fix for it as well: [http://ubuntuforums.org/showthread.php?t=385886](http://ubuntuforums.org/showthread.php?t=385886)

---

### Post by Thaismai on 2008-11-13
So the corrupt dpkg is one issue, and I'll try to fix that when I'm in ubuntu later with the information you provided in the link. 

The other issue is why the 800mb of extra space I left Ubuntu has filled up so quickly whilst only downloading about 30mb of updates. How much space does the typical Ubuntu install take up? If there is a big file of empty space somewhere, how can I find it and fix this problem? 

Is there a way of rolling back the updates, and could that remove the file(s)?

James.

---

### Post by Thaismai on 2008-11-14
I don't have permission to delete or move files, even though using it a live session I should be logged in as root??

In regards to overcoming the problem of not having any space, is it possible to increase the size of the 1.5GB space I initially set aside for Ubuntu and its loop file to 2GB? If I look at it in the partition manager is just shows it as 1.91GB with 1.47 GB used. If I can do this it won't neccesarily fix the problem but at least give me some room to move. 

James.

EDIT: I just tried to move the file in terminal to a different location and it worked. Ran 'sudo dpkg --configure -a', and that worked too, however:

Errors were encountered while processing:
 system-tools-backends
 totem-common.

Tried to run update manager again and it appears to be working! Oh no, it isn't, probably due to lack of space. OK, so the only problem at the moment appears to be lack of drive space. 

Looking at 'df -h'

```

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 981M  2.0M  979M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 981M  2.0M  979M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 981M     0  981M   0% /lib/init/rw
varrun                981M  104K  981M   1% /var/run
varlock               981M     0  981M   0% /var/lock
udev                  981M  2.8M  978M   1% /dev
tmpfs                 981M  956K  980M   1% /dev/shm
rootfs                788M  707M   41M  95% /
/dev/sdb1             2.0G  1.5G  449M  77% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 788M  707M   41M  95% /tmp
/dev/scd1             6.4M  6.4M     0 100% /media/U3 System
```

Can someone explain to me which is the mount where the Ubuntu install is located, and which mount is the space I set aside for the loop file? I'm assuming rofs and tmp.

---

### Post by geirha on 2008-11-14
It would help to know how it was created/installed. Did you follow a guide?

Anyway, / is the filesystem the packages are installed to, so that would be were you need more space, or possibly create a new partition and use it as /usr.

/tmp is mounted with tmpfs which means its stored in memory, and I assume /rofs means read only file system, so it's possibly a mounted iso-image or something?

---

### Post by Thaismai on 2008-11-14
Ok, I've resolved the problem but haven't really solved the problem. I've re-installed Ubuntu on my flash drive, this time with a utilizing the entire 2 GB for it, therefore having 1.2 GB of extra space for ubuntu.  I've installed Skype and Adobe Flash, and it looks like this:

```

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 981M  2.0M  979M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 981M  2.0M  979M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 981M     0  981M   0% /lib/init/rw
varrun                981M  104K  981M   1% /var/run
varlock               981M     0  981M   0% /var/lock
udev                  981M  2.8M  978M   1% /dev
tmpfs                 981M  260K  980M   1% /dev/shm
rootfs                1.2G  327M  831M  29% /
/dev/sdb1             2.0G  1.9G   11M 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 981M   28K  981M   1% /tmp
/dev/scd1             6.4M  6.4M     0 100% /media/U3 System
/dev/scd2             6.7M  6.7M     0 100% /media/U3 System_
/dev/sdc              7.5G  4.5G  3.0G  61% /media/CRUZER8

```

I'm going to be careful with what updates I install now. I don't see how updates can be bigger than the actual install. 

Geirha - Thanks for you help in trying to figure this one out, but in the end re-installing was going to be quicker and easier.

James.

---

### Post by pavel123 on 2008-11-26
It's a pity, but probably you'll encounter that problem again no matter how many gigabytes you use (I have [the similar problem with 4GB flash drive]("http://ubuntuforums.org/showthread.php?t=994044")).

Maybe we should commit bug-report to "live usb-creator" project.

---

### Post by pavel123 on 2008-11-27
I created [a bug report]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/302703") on launchpad.

---

### Post by CatKiller on 2008-11-27
> **Thaismai said:**
> I don't have permission to delete or move files, even though using it a live session I should be logged in as root??

Why would you think that? Ubuntu live sessions use a normal user. You can still use **sudo** in the usual way, it just won't ask you for a password.

---

### Post by CatKiller on 2008-11-27
> **Thaismai said:**
> How much space does the typical Ubuntu install take up?

4GiB is the minimum, according to the Hardy cd I've got here. That's just the install, without any extra programs installed. And not counting user data in /home.

---

### Post by pavel123 on 2008-12-03
I've figured-out [the root of the problem]("http://ubuntuforums.org/showthread.php?p=6304135#post6304135").

---


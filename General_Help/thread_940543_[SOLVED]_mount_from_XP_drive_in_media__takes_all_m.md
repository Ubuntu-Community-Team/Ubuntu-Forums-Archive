---
title: "[SOLVED] mount from XP drive in media  takes all my Ubuntu disk space"
date: 2008-10-07
forum: General Help
---

### Post by pognonec on 2008-10-07
I have 2 physically distinct HD: 1 with XP, 1 with Ubuntu. I always boot on Ubuntu, and to have access to some old files on my XP drive, I put a mount point that is present in "media" on my Ubuntu drive. 
That was done a while ago, and everything works fine.
However, I recently realized that I am running out of space on my Ubuntu drive. And I was shocked to see that the 50 Go of space used by my XP stuff on the XP drive are integrally taken into account into the "media" folder in the Ubuntu drive!!!
I thought the mount of a drive was just kind of a link to the "real" thing. How come the whole 50 Go are considered "real" on my Ubuntu drive?

---

### Post by justleen on 2008-10-07
the mount point is counted as a folder.. linux doenst see it as a drive anymore once mounted. SO yes, the diskspace is calculated over all driver (all mounts)

edit : the "df -h" command should give a better picture of your diskspace..

---

### Post by pognonec on 2008-10-07
> **justleen said:**
> the mount point is counted as a folder.. linux doenst see it as a drive anymore once mounted. SO yes, the diskspace is calculated over all driver (all mounts)

edit : the "df -h" command should give a better picture of your diskspace..

Thanx justleen for your quick feedback.
So if I understand well, with a 100 Go Ubuntu drive with only 10 Go of "real files" and a mount from another HD with 90 Go of files, my Ubuntu drives is indeed full? I find this weird. Is there a way of avoiding this, while keeping easy access to the 90 Go of information on the other drive? (As we say in French, "the butter AND the money from the butter")...

For information, here is my df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             150G  139G  2.7G  99% /
varrun                474M  268K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   68K  474M   1% /dev
devshm                474M  148K  474M   1% /dev/shm
lrm                   474M   39M  435M   9% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1             141G   45G   97G  32% /media/Windows HD

---

### Post by geirha on 2008-10-07
Try these commands to see disk usage. They do not count your windows filesystem.
```

sudo du --max-depth=1 -hx / 
sudo du --max-depth=1 -hx /media
sudo du --max-depth=1 -hx /home

```

My guess is you have put some stuff in /media/Windows HD while it wasn't mounted, so if /media shows alot of usage, unmount your windows partition and check what's in there.

---

### Post by pognonec on 2008-10-07
> **geirha said:**
> Try these commands to see disk usage. They do not count your windows filesystem.
```

sudo du --max-depth=1 -hx / 
sudo du --max-depth=1 -hx /media
sudo du --max-depth=1 -hx /home

```

My guess is you have put some stuff in /media/Windows HD while it wasn't mounted, so if /media shows alot of usage, unmount your windows partition and check what's in there.

When I unmount /media/Windows HD, and check its propriety in the media folder, its is empty.
To me, the three commands you suggested (see below) say I only have about 30 Go on my Ubuntu drive. But I also see:
/dev/sdb1             150G  140G  2.4G  99% /
So what is going on?? And where could "139G	/" come from??



philippe@Pognonec:~$ sudo du --max-depth=1 -hx / 
[sudo] password for philippe: 
419M	/opt
16K	/media
1.6M	/tmp
106G	/root
692M	/lib
4.0K	/srv
6.6M	/sbin
14M	/etc
0	/proc
0	/dev
348M	/var
4.0K	/initrd
2.7G	/usr
98M	/boot
4.0K	/mnt
0	/sys
30G	/home
16K	/lost+found
5.2M	/bin
139G	/


philippe@Pognonec:~$ sudo du --max-depth=1 -hx /media
8.0K	/media/Windows HD
4.0K	/media/cdrom0
16K	/media


philippe@Pognonec:~$ sudo du --max-depth=1 -hx /home
29G	/home/philippe
417M	/home/ftp
30G	/home

---

### Post by geirha on 2008-10-07
139G / is just the sum of all of the above.

However:
```
106G /root
```
You got 106GiB in root's homefolder ... better check what that is all about.

---

### Post by jerome1232 on 2008-10-07
btw to use the above commands to check out root you could do something like
```
sudo du --max-depth=1 -hx /root
``` that ought to tell you what's using up space in roots home. (maybe change max-depth to 2 if you just see a directory)

---

### Post by pognonec on 2008-10-07
Thanx to all of you, things get clearer now:

105G	/root/.local/share/Trash/files

I was using a folder on my second HD 5Windows HD) as a target for my Ubuntu daily sBackup. And I recently trashed all these old backups, from nautilus. Apparently, it somehow ended up in this folder. I suspect I can simply delete it to get space back on my Ubuntu drive (eventhough I still have a hard time understanding how come what was on the other drive ends up on my Ubuntu drive). 
Too subtle for me, I guess...

---

### Post by jerome1232 on 2008-10-07
When running nautilus as root, it puts all trash in roots trash. Just as like when you delete things as your own user it goes to your own trash.

---

### Post by pognonec on 2008-10-07
> **jerome1232 said:**
> When running nautilus as root, it puts all trash in roots trash. Just as like when you delete things as your own user it goes to your own trash.

Got it.
Thanks again to all!

---


---
title: "Not enough space?"
date: 2008-10-07
forum: General Help
---

### Post by lcruz007 on 2008-10-07
Hello!
I have been having problems copying files to my partition in Ubuntu because it seems I don't have enough space. That's not true though, because I have 20GB free on my partition I did on Windows vista.

I remember when installing Ubuntu that it asked me to choose the memory it would take for the installation or something... I selected 3 or 5 GB, does that have something to do with my problem..?

---

### Post by lcruz007 on 2008-10-07
Bump. Someone has an answer?

---

### Post by arsham on 2008-10-07
> **lcruz007 said:**
> Hello!
I have been having problems copying files to my partition in Ubuntu because it seems I don't have enough space. That's not true though, because I have 20GB free on my partition I did on Windows vista.

I remember when installing Ubuntu that it asked me to choose the memory it would take for the installation or something... I selected 3 or 5 GB, does that have something to do with my problem..?

Open a terminal and type this command, and give back the results ( tell us which partition is exactly you are reffering to )
```

df -h


```

---

### Post by nikgare on 2008-10-07
Please wait more than 21 minutes before bumping a thread

---

### Post by lcruz007 on 2008-10-08
Outcome:
```
luis@luis-laptop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      3.6G  3.5G     0 100% /
varrun               1009M  108K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   52K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
lrm                  1009M   39M  971M   4% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
gvfs-fuse-daemon      3.6G  3.5G     0 100% /home/luis/.gvfs
luis@luis-laptop:~$ 

```

I don't know what's the problem, you can see the partition I made using Windows, it has 20GB free...

[IMG]http://i26.photobucket.com/albums/c107/luis007cruz/Dibujo-1.jpg[/IMG]

---

### Post by jerome1232 on 2008-10-08
3 or 5 gigs will certainly fill up quickly (Ubuntu says it's requires at least 5GB) I know my logs take up ~3.3GB and your programs can take up quite a bit if you install alot of software.

Acording to df -h your filesystem is full for ubuntu. A little insight as to what exactly is full would be nice, if you could post the output of this command. We probably need to create a new virtual disk and migrate whatever is using up alot of space out to it.

```
du -h --max-depth=1
```

---

### Post by lcruz007 on 2008-10-08
> **jerome1232 said:**
> 3 or 5 gigs will certainly fill up quickly (Ubuntu says it's requires at least 5GB) I know my logs take up ~3.3GB and your programs can take up quite a bit if you install alot of software.

Acording to df -h your filesystem is full for ubuntu. A little insight as to what exactly is full would be nice, if you could post the output of this command. We probably need to create a new virtual disk and migrate whatever is using up alot of space out to it.

```
du -h --max-depth=1
```

I see... ok, this is the output of the code you posted...
[B]
root@luis-laptop:/home/luis# du -h --max-depth=1
4.0K	./.icons
12K	./.gnupg
du: cannot access `./.gvfs': Permission denied
4.0K	./.ssh
4.0K	./.fr-gmYACE
4.0K	./Desktop
8.0K	./.update-manager-core
4.0K	./Templates
7.0M	./.cache
932K	./.gnome2
648K	./.gstreamer-0.10
76K	./.compiz
92K	./.gconfd
1.9M	./.thumbnails
4.0K	./.themes
732K	./.purple
220K	./.evolution
697M	./.local
4.0K	./.fr-6WZW9j
4.0K	./.wapi
4.0K	./Videos
16K	./.fontconfig
101M	./.mozilla
120K	./.tomboy
464K	./.gimp-2.4
52K	./.config
16K	./.sudoku
192K	./.macromedia
8.0K	./.update-notifier
932K	./.gconf
4.0K	./Public
12K	./.dbus
287M	./Documents
16K	./.adobe
4.0K	./Music
124K	./.nautilus
4.0K	./.pulse
2.7M	./.openoffice.org2
4.0K	./.gnome2_private
440K	./Pictures
1.1G	.
root@luis-laptop:/home/luis# [/B]

---

### Post by -Zeus- on 2008-10-08
no no, you need to be in the / folder when you do that

---

### Post by lcruz007 on 2008-10-08
> **-Zeus- said:**
> no no, you need to be in the / folder when you do that

How? Like this:

[B]root@luis-laptop:/home/luis# du -h --max-depth=1
4.0K	./.icons
12K	./.gnupg
du: cannot access `./.gvfs': Permission denied
4.0K	./.ssh
4.0K	./.fr-gmYACE
4.0K	./Desktop
8.0K	./.update-manager-core
4.0K	./Templates
7.0M	./.cache
932K	./.gnome2
648K	./.gstreamer-0.10
76K	./.compiz
92K	./.gconfd
1.9M	./.thumbnails
4.0K	./.themes
732K	./.purple
220K	./.evolution
697M	./.local
4.0K	./.fr-6WZW9j
4.0K	./.wapi
4.0K	./Videos
16K	./.fontconfig
101M	./.mozilla
120K	./.tomboy
464K	./.gimp-2.4
52K	./.config
16K	./.sudoku
192K	./.macromedia
8.0K	./.update-notifier
932K	./.gconf
4.0K	./Public
12K	./.dbus
287M	./Documents
16K	./.adobe
4.0K	./Music
124K	./.nautilus
4.0K	./.pulse
2.7M	./.openoffice.org2
4.0K	./.gnome2_private
440K	./Pictures
1.1G	.
root@luis-laptop:/home/luis# [/B]

---

### Post by ju2wheels on 2008-10-08
> **lcruz007 said:**
> Hello!
I have been having problems copying files to my partition in Ubuntu because it seems I don't have enough space. That's not true though, because I have 20GB free on my partition I did on Windows vista.

I remember when installing Ubuntu that it asked me to choose the memory it would take for the installation or something... I selected 3 or 5 GB, does that have something to do with my problem..?

Just an FYI... memory (RAM) is not the same as storage space (hard drive space). I think you may have confused virtual memory (or the swap space partition that is placed on the hard drive) with hard drive partitions used for storage.

When installing you should typically have one swap partition that is 2x the amount of physical RAM your computer has. Then at least one partition with the rest of the available hard drive space for the file system.

---

### Post by iRPM on 2008-10-08
Hi,

Please write the output of the command:

```
sudo du -h --max-depth=1 /
```

---

### Post by ubunny on 2008-10-08
look up and read about Gparted and QtParted here in the forums, (take all precautions as necessary).  I once had to add more space to my ubuntu edgy or gutsy but it's been a while since I've needed it.  I recall reducing my windows partition then added it to ubuntu.  I eventually gutted windows and went 100% linux last year.

You can also pipe your disk usage reply to the sort command, ie: 

sudo du --max-depth=1 | sort -n 

will give you a list of the largest items sorted at the bottom in any directory that it's run.  Run this in the root directory /.  To get there cd / and the prompt should now have a / in it.  

The du -h in other examples means human readable but it interfers with sorting, so I omitted it.  sort -n means to sort by numeric (size).

you will have to remove enough files to allow ubuntu to run or use the rescue dvd.

Is this a brand new install?  You might just consider wiping ubuntu and redoing it with the correct partition sizes.

Given the nature of the question, I'm concerned you may not have enough experience in trying this yet, so please read more in the forums regarding partitioning.  Post your questions and we can all help sort out the steps for you.  First step here though is patience, so that you don't lose data.

;)

---

### Post by jerome1232 on 2008-10-08
Yeah I typo'd on my giving of the command sorry, I meant what iRPM has on his post.

Or you could use ubunny's version it'll work too. Because your using a wubi install the solution will be different than for someone who was running in real partitions. There's a section in the wubi wiki that explains how to create new virtual disks and move content out to them.

---

### Post by geirha on 2008-10-08
Seems you have installed ubuntu via wubi. That means that ubuntu is using a virtual harddrive, which is simply a file on your F:, and it is only using ~5GB of the windows parition you've given it. Check out the [WubiGuide](https://wiki.ubuntu.com/WubiGuide) for information on giving ubuntu more space.

---


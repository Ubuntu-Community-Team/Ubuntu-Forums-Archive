---
title: "[SOLVED] Ubuntu install won't delete previous linux os data"
date: 2008-11-16
forum: General Help
---

### Post by matthekc on 2008-11-16
I am trying to install Ubuntu over linux mint but its trying to keep all my old files and configs.  How do I get it to nuke everything.  Is this some kind of new feature?  It is droping me into a mangled broken gnome desktop.:mad:

---

### Post by Monotoko on 2008-11-16
Try formatting it

From the LiveCD
(System -> Administration -> Partition Manager)
Then format the partition

you have successfully nuked it :P
Now install ubuntu

---

### Post by matthekc on 2008-11-16
This is ugly its got locks on sda2 (my swap) and sda3 (my home) and I tried using chmod from the live cd.

ubuntu@ubuntu:~$ chmod 777 /media/disk
chmod: changing permissions of `/media/disk': Operation not permitted
ubuntu@ubuntu:~$

---

### Post by Monotoko on 2008-11-16
use sudo:

```
sudo chmod 777 /media/disk
```

This gives you root priviledges, be careful what you do with sudo!
Also, it might be a simple issue of unmounting the partitions, ensure you turn swap off (right click it in GParted and click "swap off") and unmount the other one (right click again -> unmount)

---

### Post by matthekc on 2008-11-16
I keep all my data on sda 4 

sda1 OS
sda2 swap
sda3 home
sda4 where my actual stuff resides

---

### Post by matthekc on 2008-11-16
huh sudo works on a live cd?  well I ran the command close the partition editor and reopened it. The lock is still on the partition.

---

### Post by Monotoko on 2008-11-16
Right, boot into the liveCD
make sure all partitions are unmounted

go into GParted (Partition Manager)
and delete:
sda1 OS
sda2 swap
sda3 home

dont put anything in there place, just leave it as unformatted space then when installing ubuntu, choose "use continous free space" and it should install in that space

---

### Post by matthekc on 2008-11-16
sudo rm -fR  /media/disk/kevin

It will die!

---

### Post by matthekc on 2008-11-16
oh yeah maybe umounting it will help. :lolflag:
Oh well that data will be good and gone.

---

### Post by Monotoko on 2008-11-16
/media/disk??
That means its mounted, be sure to unmount all partitions first, then use gparted, and isnt it supposed to die? (all apart from sda4)

---

### Post by matthekc on 2008-11-16
Yes data be gone is the intended goal.

Yeah I forgot to umount it in a blind rage.

I mounted it to try to delete everthing in gui file manager...
Probably not the best way to do things in retrospect.
I feel stupid.

---

### Post by matthekc on 2008-11-16
You would think after two years of linux use I would know how partitions worked.

---

### Post by matthekc on 2008-11-16
Well, I'll be back if that didn't do the trick wish me luck.

---

### Post by Monotoko on 2008-11-16
Good luck, and dont feel stupid, it was a simple mistake, also, ubuntu is new to you, it always takes a while to get used to somehing differant, especially when your getting fustrated with old data.

Also popcorn for all :D
:popcorn:

---

### Post by boof1988 on 2008-11-16
Here's some more popcorn

:popcorn:

And some rock

:guitar:

Hope it goes well...

---

### Post by matthekc on 2008-11-16
thanks for everything guys.
I'll mark this solved.

---


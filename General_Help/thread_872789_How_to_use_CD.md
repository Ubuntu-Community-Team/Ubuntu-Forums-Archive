---
title: "How to use CD"
date: 2008-07-28
forum: General Help
---

### Post by byteguy on 2008-07-28
Hello,
I'm new to Linux and I'm trying to navigate in terminal. I have a second drive hooked to my system. I can use the CD command to navigate around my boot drive but I can't figure out how to get to the second drive. I can see it is mounted on my desktop. And how can I use dir to list all the devices/mount points?

---

### Post by dje on 2008-07-28
use this to list all mounted drives:
```
mount
```
then you would get the mount point for the drive you wanted eg. /media/my_files
```
cd /media/my_files
```

hope that helps,
dje

---

### Post by fxtrem on 2008-07-28
List your devices, where they are mounted, etc.(*mounted devices**):
```
df -h
```

To navigate on the terminal on your device:
```
cd /media/<device>
```

---

### Post by byteguy on 2008-07-28
thanks, big help. so now I have navigated to it but it says permission denied. can I unlock the permissions in terminal?

---

### Post by fxtrem on 2008-07-28
> **byteguy said:**
> thanks, big help. so now I have navigated to it but it says permission denied. can I unlock the permissions in terminal?

I didn't have this problem, can you navigate in the device as superuser?

---

### Post by byteguy on 2008-07-28
I typed sudo $ first. I guess that makes me a superuser.. The permission tab in properties shows the owner as root. I can't login as root. could that be the problem. Also, the drive I am trying to access is a clients drive so there may be security features set. Client doesn't know either as a company set up the system for them. The only directory in their main folder is a lost+found dir. I am hoping all of their files are in their but i can't access it. It's probably simple but I'm just too new to Linux terminal commands. The book I have is hard to extract info from.

---

### Post by fxtrem on 2008-07-28
> **byteguy said:**
> (...) I can't login as root (...)

Try:
```
sudo -i
```

Note:
*I've edited my first post with a better way to list devices (df -h)*;)

---

### Post by byteguy on 2008-07-28
OK, gettin closer. Before it said permission denied. Now it will go to that lost+foind directory but instead if just listing lost+found, it lists it as lost+found#. How can I run the equivalent of "chkdsk" on the volume first to fix any possible problems?

---

### Post by fxtrem on 2008-07-28
Try this:
```
fsck -p -v <device>
```

Note:
*Don't use this on a mounted device.*

---

### Post by byteguy on 2008-07-28
so the command would be "fsck -p -v <sdb2>"

---

### Post by fxtrem on 2008-07-28
If sdb2 is your CD drive, yes. ;)

---

### Post by byteguy on 2008-07-28
I ran fsck, doesn't look like there were any problems. Still when I navigate to the lost+found directory and type dir, it acts like nothing is in the directory. When I double click on that folder from the desktop, it says I don't have the permission necessary to view the contents

---

### Post by fxtrem on 2008-07-28
Try this:
```

sudo mkdir /media/CD
sudo mount /dev/<CD Driver, e.g. cdrom, scd0, sdb2> /media/CD

```
Then to navigate on the CD driver:
```

cd /media/CD

```

---

### Post by bodhi.zazen on 2008-07-28
> **byteguy said:**
> I ran fsck, doesn't look like there were any problems. Still when I navigate to the lost+found directory and type dir, it acts like nothing is in the directory. When I double click on that folder from the desktop, it says I don't have the permission necessary to view the contents

lost+found is a system file. You are describing normal behavior.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by byteguy on 2008-07-28
so how can I view what is in that folder?

---

### Post by byteguy on 2008-07-28
The thread title might be misleading..I'm not trying to work with my CD rom. I was trying to work with change directory..

---

### Post by fxtrem on 2008-07-28
Did you tried this? It might work ;):

> **fxtrem said:**
> Try this:
```

sudo mkdir /media/CD
sudo mount /dev/<CD Driver, e.g. cdrom, scd0, sdb2> /media/CD

```
Then to navigate on the CD driver:
```

cd /media/CD

```

---

### Post by byteguy on 2008-07-28
sorry, will have to get back to this later..I'll try it then. Thanks for the help..

---

### Post by fxtrem on 2008-07-28
Ok, see you.

---


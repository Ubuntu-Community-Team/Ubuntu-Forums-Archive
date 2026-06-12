---
title: "How do I run cron as root ?"
date: 2008-09-19
forum: General Help
---

### Post by ricemark20 on 2008-09-19
I am trying to create a cron job to run rsync as root while I'm logged in as user. I'm just backing up my /home but get an error unless I run as root.

```
mark@mark-desktop:~$ rsync -avr /home/mark /media/sda1/home
```

```
rsync: chgrp "/media/sda1/home/mark/.TileRacer/0.7/tmp/Impostor.General.NormalTree.mesh.128.png" failed: Operation not permitted (1)
rsync: chgrp "/media/sda1/home/mark/.TileRacer/0.7/tmp/Impostor.General.pinetree_01.mesh.128.png" failed: Operation not permitted (1)
rsync: chgrp "/media/sda1/home/mark/.TileRacer/0.7/tmp/Impostor.General.pinetree_02.mesh.128.png" failed: Operation not permitted (1)
rsync: chgrp "/media/sda1/home/mark/.TileRacer/0.7/tmp/Impostor.General.pinetree_03.mesh.128.png" failed: Operation not permitted (1)
mark/.TileRacer/0.7/tmp/lightmaps/
rsync: chgrp "/media/sda1/home/mark/.TileRacer/0.7/tmp/lightmaps" failed: Operation not permitted (1)

```

I get a ton of errors like this.

---

### Post by forger on 2008-09-19
what's the output of:
```
ls -ld /home/mark  /media/sda1/home /media/sda1
```

---

### Post by forger on 2008-09-19
Is your destination partition formatted as fat32? fat32 can't handle groups/permissions :)
[http://ubuntuforums.org/showthread.php?t=472454](http://ubuntuforums.org/showthread.php?t=472454)
[http://ubuntuforums.org/showthread.php?t=624198](http://ubuntuforums.org/showthread.php?t=624198)

I would suggest using the tar command instead:
**[COLOR="Red"]WARNING: Untested command, use at your own risk![/COLOR]**
```
tar --update --preserve --recursion -f /media/sda1/home.tar /home/mark/
```

---

### Post by ricemark20 on 2008-09-19
> **forger said:**
> what's the output of:
```
ls -ld /home/mark  /media/sda1/home /media/sda1
```

```
mark@mark-desktop:~$ ls -ld /home/mark  /media/sda1/home /media/sda1
drwxr-xr-x 130 mark mark    12288 2008-09-19 07:08 /home/mark
drwxrwx---   1 root plugdev  8192 2008-09-18 19:54 /media/sda1
drwxrwx---   1 root plugdev     0 2008-09-16 03:52 /media/sda1/home

```

---

### Post by ricemark20 on 2008-09-19
> **forger said:**
> Is your destination partition formatted as fat32? fat32 can't handle groups/permissions :)
[http://ubuntuforums.org/showthread.php?t=472454](http://ubuntuforums.org/showthread.php?t=472454)
[http://ubuntuforums.org/showthread.php?t=624198](http://ubuntuforums.org/showthread.php?t=624198)

I would suggest using the tar command instead:
**[COLOR="Red"]WARNING: Untested command, use at your own risk![/COLOR]**
```
tar --update --preserve --recursion -f /media/sda1/home.tar /home/mark/
```

<sigh>  I checked gparted, and it's formatted in ntfs.  Guess I need a separate ext3 partition.

---

### Post by hyper_ch on 2008-09-19
(1) run
```

sudo crontab -u root -l

```

(2) if step 1 does not return anything then do
```

cd /root
sudo nano cron.txt

```

(3) add the according jobs you want to run as root

(4) save and exit the cron.txt file

(5) add the cron.txt to root cron
```

sudo crontab cron.txt

```

(6) verify if it was added:
```

sudo crontab -u root -l

```

---

### Post by ricemark20 on 2008-09-19
> **hyper_ch said:**
> (1) run
```

sudo crontab -u root -l

```

(2) if step 1 does not return anything then do
```

cd /root
sudo nano cron.txt

```

(3) add the according jobs you want to run as root

(4) save and exit the cron.txt file

(5) add the cron.txt to root cron
```

sudo crontab cron.txt

```

(6) verify if it was added:
```

sudo crontab -u root -l

```

I tried it with and without root in front of rsync.  Nothing happened.

```
50 10 * * * rsync -avrpE /home/mark /media/sda1/home >~/logs/myhomelog_dailytest.log
```

I even did a test that wrote the contents of a directory to a text file.
That worked fine.

---

### Post by hyper_ch on 2008-09-20
Did you look whether you have the output in /root/logs/myhomelog_dailytest.log?

When you run it as root, then /root is the homefolder as indicated by ~

---


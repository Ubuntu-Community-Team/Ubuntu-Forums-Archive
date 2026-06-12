---
title: "Hard drive fills up &amp; wont stop"
date: 2008-09-15
forum: General Help
---

### Post by collinp on 2008-09-15
&#65279;[SIZE=3][SIZE=2]Hey guys, im having trouble isolating the cause of my hard drive filling up slap full, a du /* leads me to the .wine directory in /home, but it has always been the size it is. I cant find anywhere else it could be going. Help? Oh, and when i free up space, it gets taken up just as fast, so that links to something running, but i dont see anything. Oh, and i just uninstalled the entire (or so i thought) Kubuntu KDE4 desktop.[/SIZE]
[/SIZE]

---

### Post by Vivaldi Gloria on 2008-09-15
Try cleaning root's trash.

---

### Post by drs305 on 2008-09-15
Check out the Disk Full link in my signature line:[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

It explains how to find the hidden trash files on your system and how to delete system trash files which are taking up space.

---

### Post by collinp on 2008-09-15
Here is the output of du -sh /*:
```

5.2M    /bin
32K    /bobotpp
36M    /boot
4.0K    /bot.log
0    /cdrom
260K    /dev
20M    /etc
5.0G    /home
4.0K    /initrd
0    /initrd.img
0    /initrd.img.old
285M    /lib
3.0M    /lib64
16K    /lost+found
48K    /media
4.0K    /mnt
4.0K    /opt
du: cannot access `/proc/24249/task/24249/fd/3': No such file or directory
du: cannot access `/proc/24249/task/24249/fdinfo/3': No such file or directory
du: cannot access `/proc/24249/fd/3': No such file or directory
du: cannot access `/proc/24249/fdinfo/3': No such file or directory
0    /proc
1.4M    /root
6.9M    /sbin
4.0K    /script.log
4.0K    /srv
0    /sys
956K    /tmp
3.1G    /usr
431M    /var
0    /vmlinuz
0    /vmlinuz.old

```Also, there is nothing in root's trash directory (/root/.local/share/Trash/files). Also, i am thinking there is some odd backup utility or something left over from KDE4 that i missed when i was going through uninstalling, and it may be running in the background because every time i free up space it gets taken back up again not long after. Yet I see nothing that may be related to KDE in ps x.

---

### Post by Dr Small on 2008-09-15
How big is your hard drive? I don't see anything that is taking up a huge amount of space, besides /usr with 3GBs.

---

### Post by collinp on 2008-09-15
> **Dr Small said:**
> How big is your hard drive? I don't see anything that is taking up a huge amount of space, besides /usr with 3GBs.

18GBs

---

### Post by collinp on 2008-09-15
Oh, and a df -h shows this:
```
/dev/sda1              18G   17G     0 100% /

```

---

### Post by collinp on 2008-09-15
Bump

---

### Post by shaggy999 on 2008-09-15
Try running the 'du' command sudo. This will allow it to traverse directories owned by root, which may be where the offending file(s) can be found. It very well could be something as simple as a program trying to run and constantly crashing, producing error logs that are filling up the hard drive along the way.

Run 'du' sudo and report back the results.

---

### Post by shaggy999 on 2008-09-15
I didn't mean to say 'owned by root' but 'only traversable by root'.

---

### Post by cprofitt on 2008-09-15
Run baobab to see where the file usage is large

---

### Post by Zidaps on 2011-09-26
Hi, 

Has anyone found a solution to this?? I have a 64GB main hard drive that I am backing up onto a 160GB hard drive.

After cron runs rsync 2x the destination 160GB drive is full... Whats going on here... this is what I'm doing.

```
sudo rsync -H -a --delete /  /media/destination/filesysbackup
```

---

### Post by Zidaps on 2011-09-30
In case someone is looking for this. Found a solution :guitar: with the help of someone by the name of "BasketCase" on the rsync IRC chat...

Use the following:

> sudo rsync -H -a --delete --one-file-system /copyfrom/folder    /media/backupto/folder

if you get an error for some reason as I did:

> rsync: readlink_stat("/home/username/.gvfs") failed: Permission denied (13)
IO error encountered -- skipping file deletion
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

include the following in your terminal command: --exclude=.gvfs

That should solve the problem. Worked for me. :KS

---


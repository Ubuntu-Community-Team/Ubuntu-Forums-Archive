---
title: "[SOLVED] The Mystery of the FULL HD!!! Please Help"
date: 2008-08-28
forum: General Help
---

### Post by coppercow on 2008-08-28
Full disclosure; I am a week (5 days really) into Kubuntu a life long Winuman (Windows Human) trying to escape the matrix. 

Here is what I have:

Dell Inspiron 1525
Win XP 
Kubuntu (the one I downloaded last week)

2 partitions created at boot.I mounted my ntfs and find it in the media folder. My home folder is 15.7GB when I click into it i select all the folders get properties and they all add up to 1.2GB I can't find the remaining 14.5GB 

Can someone please help me I want to use Kubuntu. :confused::confused: I don't know how to find the offending files in my home directory. :confused::confused:

using [COLOR="Red"]du -ks /* | sort -n[/COLOR] I get:


du: cannot access `/proc/8931/task/8931/fd/4': No such file or directory
du: cannot access `/proc/8931/task/8931/fdinfo/4': No such file or directory
du: cannot access `/proc/8931/fd/4': No such file or directory
du: cannot access `/proc/8931/fdinfo/4': No such file or directory
0       /cdrom
0       /initrd.img
0       /proc
0       /sys
0       /vmlinuz
4       /initrd
4       /mnt
4       /opt
4       /srv
16      /lost+found
84      /dev
88      /tmp
544     /root
5316    /bin
7092    /sbin
13788   /etc
19108   /boot
171184  /lib
624212  /var
2390976 /usr
15959864        /home
102387217       /media

---

### Post by drs305 on 2008-08-28
I've written a fairly inclusive tutorial on finding hidden trash on your system, which could be the problem. 

[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

If you have an questions from the site I'll be glad to answer them.

---

### Post by coppercow on 2008-08-28
/home/[COLOR="Red"]username[/COLOR]/.strigi/clucene

This Directory has a bunch of files one is 6.5gb large... :-k

_oe2x.fdt  <- largest
.cfs <- bunch of these ranging from 800mb to little.

What is this? Can I safely delete them? How do i prevent from happening?

---

### Post by coppercow on 2008-08-28
ok the problem was strigi - desktop search. WHAT A POS!

seems the index's database goes crazy and grows without bounds (well not really your disk space is the only limit) after a search and some help I found a bug report on it not sure if I can post links so I will not do so.

so i uninstalled strigi then used nautilus to delete the folders.

drs305 Thanks for all the help really appreciated 8-).

---

### Post by mb_webguy on 2008-08-28
Yeah, desktop search apps apparently tend to be a problem on any OS.  I had a problem on my old XP system with Google desktop search hogging all of my system resources because it was constantly indexing my files.  One of the first things I do when installing Ubuntu is disable the Tracker desktop search...

---


---
title: "Hard Drive Space Being Chewed Up"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by Transport Man on 2006-09-09
Hi all. I'm starting this thread to find out if anyone has experienced similar problems with hard drive space on Ubuntu Linux 6.06 for x86. 

I have installed Ubuntu on my laptop in a dual boot configuration with windows XP Professional the hard drive is 40GB and Ubuntu is on a 5GB partion i also have installed the KDE desktop environment. Whilst i have been running Ubuntu i have noticed that the free space on the hard drive decreases very slowly whilst the computer is left running idle that is without me installing or writing any files to the drive the free space that disapperes does not seem to come back and at one point all the space on the drive dissappered which stopped me from being able to log into Ubuntu completely. 

If anyone knows how to fix this problem or has had a similar problem your help would be greatly appreciated.

---

### Post by eightball01 on 2006-09-09
Well, Ubuntu is around 2 GB on a fresh install. KDE takes up more space. Could be tmp files that are created while using. If you're going online, then cache and such will also come into play.

---

### Post by ijanos on 2006-09-09
Install baobab, with it you can trace which is wasting your disk.

ps: Oh and [HERE](http://doc.gwos.org/index.php/RemoveJunkFiles) is a good howto too.

---

### Post by Transport Man on 2006-09-10
Hi again. 
I thought of temp files however I tried a test with the computer where I turned it on and left it sitting on the desk without opening any programs. I found that hard drive space was roughly being chewed up at around 1MB per minute. That is without any programs open and I also don't have any other things running in the background.

---

### Post by ijanos on 2006-09-11
> **Transport Man said:**
> That is without any programs open and I also don't have any other things running in the background.

:shock: 1MB/m is far beyond normal behavior. There MUST be a program which is using this amount of disk. Which program you tried? Open a terminal and run *top* and watch, hopefully the evil process will show up and start eating your processor too.

---

### Post by Timothy Butwinick on 2006-12-15
I have the exact same problem as Transport Man on my 4 GB hard disk.

```
jonne@LINUX:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             3,5G  3,2G  106M  97% /
varrun                125M  132K  125M   1% /var/run
varlock               125M  4,0K  125M   1% /var/lock
udev                  125M   80K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   18M  107M  15% /lib/modules/2.6.15-27-686/volatile
/dev/hdc1             4,0G  2,2G  1,6G  58% /hdc
/dev/hdd1             4,0G  207M  3,6G   6% /hdd

```
The system is installed on hda1. 

This thread [http://ubuntuforums.org/showthread.php?t=141359&highlight=eating+hard+disk+spacev](http://ubuntuforums.org/showthread.php?t=141359&highlight=eating+hard+disk+spacev) speaks of emptying the ~/.Trash directory, but that did not help me much.
Furthermore, guides like [http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles) only give me about 20 MB more space. 

```
sudo du -hc --max-depth=1
```
gives me this:
```
48K     ./lost+found
181M    ./var <======
2,1G    ./hdc
79M     ./hdd
16M     ./etc
8,0K    ./media
4,3M    ./bin
37M     ./boot
96K     ./dev
277M    ./home
4,0K    ./initrd
347M    ./lib <=======
4,0K    ./mnt
6,5M    ./opt
du: `./proc/5439/task': No such file or directory
du: `./proc/5439/fd': No such file or directory
258M    ./proc <========
5,5M    ./root
11M     ./sbin
4,0K    ./srv
0       ./sys
88K     ./tmp
2,3G    ./usr <========
5,5G    .
5,5G    total

```

As you can see /lib, /var, /proc and /usr are the biggest directories. My guess is that some log file is growing in these directories while I use the computer, since I do not have to save or install anything for this to happen. Does anybody know of possible "problem files"?

---

### Post by hikaricore on 2006-12-15
There have been problems on some releases with the: *~/.xsession-errors* file.  You may want to have a look to see if this is what's causing it.

```
ls -l ~/.xsession-errors
```

If it is the problem, just soft link the damn thing to /dev/null and it won't happen again hehe.

---

### Post by Timothy Butwinick on 2006-12-15
Nope: It's only 3 kB.

---

### Post by mcduck on 2006-12-15
how are the file sizes in /var/log? There might something wrong on your machine that fills some log file with error messages..

anyway, with both Gnome and KDE it's not a surprise that you are low on disk space with a 5GB partition.

---

### Post by Timothy Butwinick on 2006-12-15
```
jonne@LINUX:/var/log$ du -h
60K     ./cups
48K     ./gdm
4,0K    ./news
4,0K    ./unattended-upgrades
204K    ./installer
8,0K    ./avast4
72K     ./samba
4,0K    ./clamav
36K     ./nessus
4,0K    ./mldonkey
2,4M    .

```

i.e. 2.4 MB.

Also, I'm (kind of) using Xubuntu, not Gnome or KDE. I first installed Ubuntu from the live CD, then downloaded the Xfce-packages. Perhaps this is the problem? I should probably have used the normal Xubuntu CD.

Well, then: Time for a fresh system reinstallation!

---


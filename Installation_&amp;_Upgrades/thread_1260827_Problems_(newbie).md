---
title: "Problems (newbie)"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by all4enjoy on 2009-09-08
Hi i am a newbie to ubuntu..
 
so i downloaded some themes for my system.. but in 22% it shows some errors that there is not much space ..what to do for that.. pls help me.
 
 
and i opened root folder but it's not letting me in .....but i am the administrator ..
 
whats the prob pls help me

---

### Post by oboedad55 on 2009-09-08
> **all4enjoy said:**
> Hi i am a newbie to ubuntu..
 
so i downloaded some themes for my system.. but in 22% it shows some errors that there is not much space ..what to do for that.. pls help me.
 
 
and i opened root folder but it's not letting me in .....but i am the administrator ..
 
whats the prob pls help me

Do you have a dual boot setup with Windows of some kind? It looks like your Ubuntu partition is too small. Tell us how you set up your box and we can help you. As for the /root, unlike Windows, in Linux you are not an administrator. You are a user with privileges. It's good that you can't access /root. You don't need to, and you can cause serious damage if you could. Post back with more info.

--Jon

---

### Post by presence1960 on 2009-09-08
Boot into ubuntu, open a terminal and run this command ```
df -h
```
paste the output back here.

---

### Post by sahabcse on 2009-09-08
past the o/p of

cd /
sudo du -csh ./*

---

### Post by presence1960 on 2009-09-08
> **sahabcse said:**
> past the o/p of

cd /
sudo du -csh ./*

that command only tells you the size of the directories in /. it does not tell you how full they are. here is my output of df -h:
```

raz@raz-desktop:~$ df -h
Filesystem            Size  Used Avail [COLOR="Red"]Use%[/COLOR] Mounted on
/dev/sda1              18G  5.0G   12G  30% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  108K  2.0G   1% /var/run
varlock               2.0G  4.0K  2.0G   1% /var/lock
udev                  2.0G  188K  2.0G   1% /dev
tmpfs                 2.0G  848K  2.0G   1% /dev/shm
lrm                   2.0G  2.5M  1.9G   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdc1             129G   44G   79G  36% /media/data
raz@raz-desktop:~$ 

```

df -h is much more useful in this case. here is the output of the other command:

```
raz@raz-desktop:~$ cd /
raz@raz-desktop:/$ sudo du -csh ./*
[sudo] password for raz: 
7.1M	./bin
41M	./boot
0	./cdrom
1.1M	./dev
15M	./etc
du: cannot access `./home/raz/.gvfs': Permission denied
812M	./home
0	./initrd.img
0	./initrd.img.old
357M	./lib
11M	./lib32
0	./lib64
16K	./lost+found
44G	./media
4.0K	./mnt
230M	./opt
du: cannot access `./proc/10906/task/10906/fd/3': No such file or directory
du: cannot access `./proc/10906/task/10906/fdinfo/3': No such file or directory
du: cannot access `./proc/10906/fd/3': No such file or directory
du: cannot access `./proc/10906/fdinfo/3': No such file or directory
0	./proc
2.6M	./root
9.2M	./sbin
4.0K	./selinux
4.0K	./srv
0	./sys
56K	./tmp
2.7G	./usr
775M	./var
0	./vmlinuz
0	./vmlinuz.old
49G	total
raz@raz-desktop:/$ 

```

certainly not as helpful if trying to determine how much of a partitions capacity is used.

---

### Post by sahabcse on 2009-09-08
As per your output your system has sufficient space to save data. Please paste the o/p of

#sudo fdisk -l

---

### Post by presence1960 on 2009-09-08
> **sahabcse said:**
> As per your output your system has sufficient space to save data. Please paste the o/p of

#sudo fdisk -l

:guitar: I am not the one with the problem. I was just just making a comparison between the two commands...LMAO

df -h is better for the job!

---


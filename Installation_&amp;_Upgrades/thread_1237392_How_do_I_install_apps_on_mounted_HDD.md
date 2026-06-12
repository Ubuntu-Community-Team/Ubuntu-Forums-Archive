---
title: "How do I install apps on mounted HDD?"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by Kreaninw on 2009-08-11
I am wonder that why I cannot choose the place where to install my apps. I want to install it in another HDD in my PC too.

Exemple : when I double click .deb file, it never ask me where to install my app. Like when I install some apps from Applications>Add/Remove... Those will install directly to my Filesystem HDD, when I was use windows I can choose the place where to install anything.

I think my HDD will full of apps and games someday and it will force me to go back to MS Windows.

Please help me, I really love Ubuntu. It's much better than MS Windows.


ps.I am not well in English, sorry.

---

### Post by phillw on 2009-08-11
A lot of the Apps in Linux are quite small, when compared to windows.

If you are concerned about low disk space for Ubuntu, you could look at re-sizing some of the exisiting 
areas, provided that the actual disk itself is not getting totally full.

if you drop into terminal mode and type 

```
df -h
```You should get something like this ...

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              39G   13G   25G  34% /
tmpfs                   497M        0  497M   0% /lib/init/rw
varrun                  497M  132K  497M   1% /var/run
varlock                497M        0  497M   0% /var/lock
udev                    497M  144K  497M   1% /dev
tmpfs                   497M   92K  497M   1% /dev/shm
lrm                       497M  2.2M  495M   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda1              35G   22G   14G  62% /media/sda1


```The bits we are intrested in are

/dev/sda3 -->  This holds my Linux Installation, you can see I have set aside 39GB, used 13G and have 25GB left free --- This is plenty, unless you are downloading DVD's !!

/dev/sda1 -->  This holds my Vista Installation.  It has a total allowed size of 35GB, used 22GB and free 14GB.

(You may need to mount your Windows Area for it to show - not sure, mine is set to auto mount)

If you find that your linux area is getting short of room AND you have plenty of spare room on your Windows area, you can resize both, to take area from Windows & give it Linux. Using GParted. A good tutorial for using Gparted can be found here..

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Regards,

Phill.

---

### Post by Kreaninw on 2009-08-11
Thank you for your answer.

But I think, it should include something like this to be an option. It's true that nowadays we have a hurge HDD in the market waiting for us(and some of our money). But it's a very basic option for a user to be choose. Today games for linux have a lot than before, it will eat up your HDD in someday and you will force to remove some. When I move from MS Windows to Linux, I can't believe the game for Linux will be this much. I think in the future it will be much more than this. And when I think about it, I can't shake this wonder away from me. With only my single HDD, it may be not enough.

In this stage I can say that it's a BIG PROBLEM!!!

---

### Post by shredder12 on 2009-08-11
Well, there are a few things i know which may solve your problem..
consider these options of dpkg
```
       --instdir=dir
              Change default installation directory which refers to the directory where packages are to be installed. instdir is also  the  direc&#8208;
              tory  passed  to  chroot(2) before running package&#8217;s installation scripts, which means that the scripts see instdir as a root direc&#8208;
              tory.  (Defaults to /)

       --root=dir
              Changing root changes instdir to dir and admindir to dir/var/lib/dpkg.

```

so when you are trying to install a .deb file.. using this command will probably solve your problem..
```
sudo dpkg -i --instdir=your_dir package.deb
```

i m not sure but i hope this will work..

and as the --root attribute says.. using it might change your installation directory
You should at least give it a try..
Hope it helps..

---

### Post by Kreaninw on 2009-08-11
Thank you very much.:KS

---

### Post by shredder12 on 2009-08-11
netime... :)

---


---
title: "New to Ubuntu (two questions: Update and Program Install)"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by tonydesu on 2009-08-25
Howdy,

I just decided to play around with Ubuntu, and I really like it. So far, there are only two things I cannot figure out:

1.  When I installed Ubuntu, I made a partition for it, but I didn't have any choice about the size. Am I crazy? Did I miss it? I am asking because I need to update everything and have some space to install a few programs, but it says that I don't have enough space to do that. Of course my hard drive is plenty big enough with over 70GB of free space, so I am wondering what to do about that. Any help? Thanks so much!!!

2.  How do I install programs? I read the help page on the Ubuntu website, but I still didn't get what I wanted. I want to download and install the VLC Media Player, and I tried to do what it said, but maybe cause I am switching from Windows, I am totally confused. Is there any simple step-by-step guide for that?

Anyways, I am having fun with the OS and I am eager to continue using it. Thanks for the help and for the software! :KS

---

### Post by slakkie on 2009-08-25
Diskspace and updates:

You can have a look at how much space you are using by executing the following commands in a terminal:

```

df -kh

```

With fdisk -l you can look at how your disk is partitioned, but you need admin rights to view this. Execute in in a terminal:

```

sudo fdisk -l 

```

With gparted you can change your partitions, but this cannot be done on a running system (because the partitions are mounted. Grab the livecd of gparted, boot from it and enlarge your partitions: 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Installing software:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

In short regarding software installations:

aptitude will become your best friend for maintaining packages (installing/removing/searching).

do-release-upgrade will become your friend when you want to upgrade Ubuntu to a newer release.

---

### Post by raymondh on 2009-08-26
As slakkie hinted, open a terminal (applications > accessories) and type

```
df -h
```

* you will be prompted for your password which you cannot view when you type-in

df-h will show you allocations and used amounts.  What you are looking for is root (/) which is where your ubuntu system files reside.  Chances are, you have the 2.5GB install which can happen if/when you opt to install Side-by-side and forget to use the slider to allocate sizes for windows and Ubuntu.

If my hunch is true, you have 2 options:

1.  You can resize root (/) .... enlarging it (hence taking space from somewhere)

2.  Re-do the install (which means deleting the existing installations and starting anew)

Your choice.  Again, I may be wrong with my hunch.  If so, post back the output of above df-h and,

```
sudo fdisk -l
```

small L, not 1, nor I.

Either way, some things to start doing/reading whilst cleaning this up:

1.  Back up your files.  Whenever we work on the HD, the risk increases.
2.  Some reading for reference

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

last link is the side-by-side slider.

---


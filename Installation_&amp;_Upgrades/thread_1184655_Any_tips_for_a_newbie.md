---
title: "Any tips for a newbie"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by apvm on 2009-06-11
I am going to install Vista 64 with Ubuntu togather on a 120GB drive, this will be my C drive for O/S and some temp and unimportant data only, data and program files will be on a seperate drive.
 
I read the FAQ and understand that I should install Vista 1st and then Ubuntu and have at least 10GB of disk space for it, I wonder if 10GB is enough? and Can Ubuntu access my second drive to install programs and store data without changing anything on my second drive? btw the second drive is a 500GB NTFS formmatted Tia

---

### Post by raymondh on 2009-06-11
> **apvm said:**
> I am going to install Vista 64 with Ubuntu togather on a 120GB drive, this will be my C drive for O/S and some temp and unimportant data only, data and program files will be on a seperate drive.
 
I read the FAQ and understand that I should install Vista 1st and then Ubuntu and have at least 10GB of disk space for it, I wonder if 10GB is enough? and Can Ubuntu access my second drive to install programs and store data without changing anything on my second drive? btw the second drive is a 500GB NTFS formmatted Tia

Hello AVPM,

Welcome to the community.

Some tips:

-  Try the liveCD (without any changes) and see how your system specs react to it.  It is usually a good indicator of things to come
-  Vista + Ubuntu has been the preferred ... however, it is also possible to do a Ubuntu + Vista with some editing later on.
-  8-15 GB seems to be the norm.  It really depend on how and what you use ubuntu for.  I use 20GB as I tend to grow my install fat and I fear that resizing later on may lead to corrupt data.  Also, I use a separate partitions for /, /home, /usr
-  With regards to SWAP, that will depend if you suspend a lot.  As you know, swap is there to back-up your RAM.  Most common is 1-1.5GB swap although I have seen some installs with 4GB swap (as they have followed the conventional 2X ram)
-  Yes, Ubuntu can access NTSF
-  Give yourself the advantage .... read the stickies in the forum and the official ubuntu pages as well as the release notes

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes)

-  Also, get active in launchpad.

Good luck on your adventure and post back.  The forum and its' members are there to guide you.

Regards,
-

---

### Post by apvm on 2009-06-11
Thanks, I have the ubuntu 9.04 Destop Edition CD so I suppose that is ithe live cd, anyway will do the install this weekend and post back...thanks for the tips.

---

### Post by merlinus on 2009-06-11
Very important -- once vista is installed, use its disk management tool to shrink its partition, or you may run into many problems.  Also, defrag before shrinking.

Then you can use the live cd for installing ubuntu.

10G for / is plenty as long as you will not be installing loads of apps.  If you will be using a shared partition for data, then /home can be 5-7G.  Swap is good at 1.5.

If using a shared data partition, format it as ntfs so both oses can read and write to it.

---

### Post by ezsit on 2009-06-11
This really depends on how you plan to use the OS's. If you want to do any audio/video work in Ubuntu I would suggest a root (/) of about 20gb and /home with another 20gb. If you install Ubuntu into one root partition and a swap partition I would not make root any smaller than 20gb. If you simply want to play with Ubuntu without relying on it, than just use the Wubi install and Ubuntu will get installed just like a Windows program in your C: drive.

---

### Post by apvm on 2009-06-11
Not a game player, I only use the computer to convert my home made video to dvd with DVD Flick (a freeware) and web browsing, the usual stuff.  If I can find a program that is like DVD Flick which works with Ubuntu, I'll most likely quite windows for good as I am sick of paying for the O/S every 5 years if not sooner.

---

### Post by sanemanmad on 2009-06-11
> **apvm said:**
> Not a game player, I only use the computer to convert my home made video to dvd with DVD Flick (a freeware) and web browsing, the usual stuff.  If I can find a program that is like DVD Flick which works with Ubuntu, I'll most likely quite windows for good as I am sick of paying for the O/S every 5 years if not sooner.

I use a homemade script for my videos:)

---

### Post by ezsit on 2009-06-14
> I only use the computer to convert my home made video to dvd

There are several apps that might do what you want, DeVeDe, Kino, Avidemux, and QDVDAuthor. However, you will want at least 8-16 GB of free, working space in your / and maybe in your /home directories so video editing and compilation has space to work. Take this into account when partitioning.

---


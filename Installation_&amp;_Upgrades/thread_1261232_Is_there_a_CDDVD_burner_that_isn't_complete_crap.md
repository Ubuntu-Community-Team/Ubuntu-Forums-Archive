---
title: "Is there a CD/DVD burner that isn't complete crap?"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by Ken1 on 2009-09-08
I have tried all the burners.  For example Gnome baker just crashes randomly.   Brasero freezes on me.  I'm getting really pissed off here.  I can't burn a simple CD without it screwing up.  I'm ready to format my hardrive and give up on this stupid linux experiment.

---

### Post by rob-ward on 2009-09-08
What are your trying to burn, is it just data, an iso image and audiocd ?

What is your cd/dvd writer?

you could try xcdroast or k3b but it really depends what y7our are trying to burn.

---

### Post by StuartN on 2009-09-08
From the command line "growisofs -dvd-compat -Z /dev/hdc=dvd.iso" should burn a DVD from an ISO file. If this does not work faultlessly then you probably have a system fault that will affect any disc burning package you install.

---

### Post by Ken1 on 2009-09-09
I'll take both of your suggestions into account.  I don't quite want to give up on learning Ubuntu yet, however...as an experiment I decided to partition my hard drive and install Kubuntu on the new partition.  I've had exactly none of the problems I've had with Ubuntu.  I can burn disks.  It actually responds to the command lines that are posted in this forum.  Programs in general are far more stable.  Basically all of the ills I've been having with Ubuntu haven't shown themselves with Kubuntu.  I think 1 of 2 things is possible.

1. The latest version of Ubuntu is of a lower quality than the latest Kubuntu (both are jaunty)
2. perhaps theres a bad sector on the Ubuntu portion of my hard drive which is causing errors.

---

### Post by AlexanderDGreat on 2009-09-09
Hi I'm using k3b. Never failed me so far.

I've burned ISO, and ripped dvd's.

---

### Post by infinitejones on 2009-09-09
Have you tried the command line suggestion given in the third post, in Ubuntu (not Kubuntu)? 

The reason I ask is that all of the graphical burning software, whether it's gnome-based (Gnomebaker, Brasero) or KDE-based (K3B or whatever's in Kubuntu these days) are basically all just graphical ways of telling your computer what you want to do, so that it can automatically put together the command line for you.

In other words, when it comes to burning a CD or a DVD, as far as your computer's concerned, it makes no difference whether you're using Kubuntu or Ubuntu. That's just the decoration. The command line probably is the same underneath it all.

So, if you try the command line in Ubuntu (not Kubuntu), the result will be one of two things:

1) It won't work, which means there's a problem with your hardware, not Ubuntu
2) It will work, which means that it's the Ubuntu or Gnome part of things that's causing the problem, as you suspected. So try re-installing Ubuntu, and then see if it works.

---

### Post by presence1960 on 2009-09-09
> **Ken1 said:**
> I'll take both of your suggestions into account.  I don't quite want to give up on learning Ubuntu yet, however...as an experiment I decided to partition my hard drive and install Kubuntu on the new partition.  I've had exactly none of the problems I've had with Ubuntu.  I can burn disks.  It actually responds to the command lines that are posted in this forum.  Programs in general are far more stable.  Basically all of the ills I've been having with Ubuntu haven't shown themselves with Kubuntu.  I think 1 of 2 things is possible.

1. The latest version of Ubuntu is of a lower quality than the latest Kubuntu (both are jaunty)
2. perhaps theres a bad sector on the Ubuntu portion of my hard drive which is causing errors.

It is definitely #2. I use Ubuntu 9.04 and all those burning softwares work perfectly .

---

### Post by presence1960 on 2009-09-09
> **Ken1 said:**
> I have tried all the burners.  For example Gnome baker just crashes randomly.   Brasero freezes on me.  I'm getting really pissed off here.  I can't burn a simple CD without it screwing up.  I'm ready to format my hardrive and give up on this stupid linux experiment.

learning a new OS can be a daunting challenge. Expect a steep learning curve as this [article]("http://linux.oneandoneis2.org/LNW.htm") explains.

That is why a lot of people dual-boot Linux with Windows. if they get jammed up in Linux, they can boot to windows and complete what they need to do. Then come back and give the time needed to research and learn.

If it bothers you that much it will be ok if you go back to windows. There is no shame in using windows. Linux is not in competition with windows. linux exists for those who want to use it. Although some vocal proponents of Linux will lead you to believe that Linux itself is at war with windows and you are "less than" if you use windows. That is pure poppycock!

So in the final analysis you must use whichever OS best suits your needs.

If you stick with linux and really want to learn it I have a couple of pointers:
1. Drop the ego and forget what you know about windows. most of it will not help you here.
2. Remember how it was when you first started using windows! I am sure you didn't know squat. You had to learn and it was a process to get to where you are now with windows. it will be so with Linux. be patient or go back to windows. You can't have it both ways.

---


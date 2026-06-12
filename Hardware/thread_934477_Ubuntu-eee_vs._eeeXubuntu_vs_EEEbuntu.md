---
title: "Ubuntu-eee vs. eeeXubuntu vs EEEbuntu?"
date: 2008-09-30
forum: Hardware
---

### Post by BrendanM on 2008-09-30
So I just got an eee PC 901. It's a nice little machine, but the default Xandros OS is getting on my nerves a bit. I think I'm going to switch over to Ubuntu, but there seem to be several different Ubuntu versions customized for the eee PC floating around out there.

There's [eeeXubuntu]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home"), but that seems to be a bit older and not maintained so much, and also [eeeBuntu]("http://www.eeebuntu.org/") as well as [Ubuntu-eee]("http://www.ubuntu-eee.com/"). I was wondering if somebody who's tried any of these could give me some insight? What makes them different? Which one's my best bet?

I don't care at all about eye-candy (i.e. Compiz/beryl). I'd just like something that's usable, gives me access to the big library of Ubuntu software, and ideally will be updated and maintained in the future.

---

### Post by michaelkahl on 2008-09-30
I have a 900, I run Ubuntu Eee and love it.  Yesterday there was a thread covering this same question for a 901.
[http://ubuntuforums.org/showthread.php?t=933632](http://ubuntuforums.org/showthread.php?t=933632)
Seems like the OP couldn't get wireless out-of-the-box with Ubuntu Eee.  I'm not sure about other 901 users, but understand that 901 was the start of hardware change in the Eee PC's.  I'm sure someone has documentation out there about getting wireless to work though.  Good luck and I hope you enjoy.

---

### Post by michaelkahl on 2008-09-30
UPDATE:  The OP from the thread I linked above got wireless working as it turns out.  It worked out of the box with Ubuntu Eee.

---

### Post by FrankVdb on 2008-10-04
I'm running Ubuntu EEE on an EEE 901 and all I can say is that it's bloody slow. The thing came with XP installed which I found pretty slow already. Ubuntu is hardly any better. 

Worst thing of all is probably that sometimes my EEE is subject to lag lasting for several seconds, giving the impression that the thing is freezing up. This could be due to slower write cycles of the 12 gig SSD drive compared with traditional drives but I'm not sure if that's the cause. This is driving me nuts.

Anyway it's a bad idea to use Gnome on a netbook, which is not a power system by definition, so I've been wondering all the time why the people behind Ubuntu EEE chose Gnome. Gnome is far too heavy for a netbook. I have four PC's around with standard Ubuntu on them and not one of them has a fast response, let alone that a netbook could be doing any better. I'm gradually dumping Ubuntu for Mint or another distro simply for speed reasons. 

I'll be putting Linux Mint (5, XFCE Edition) on my EEE today. See if it's still so laggy.

---

### Post by michaelkahl on 2008-10-04
I ended up, on the same installation, switching over to XFCE4, and it's night and day.  
The packages are in the repos for Ubuntu Eee, so type:

$ sudo apt-get install xfce4

I'd also suggest removing the maximus program and netbook remix.  I just had trouble getting it to not load in my xfce sessions, and had to keep killing the process.  So either do a sudo apt-get purge or just got to synaptic package manager and remove them from there.

Good luck with Mint, I booted Mint 5 and decided against it when I saw that wireless wasn't working in the live environment.  Maybe there is an easy fix for that though?

---


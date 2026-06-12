---
title: "A couple of pre-installation questions"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by seakiwi on 2006-01-09
Hi  :)

I'm about to venture into the world of Linux and install Ubuntu. I did have a play with Mandrake about a year ago, but it's been so long since I used it that much of the little I learned has vanished into thin air!

I've decided this time to install a second HD and dedicate it to Ubuntu. I figure that hopefully doing it that way will be a bit less scary than last time, when I partitioned my Windows drive to install Mandrake. 

The first question I have is probably a stupid one but ...

The new drive I'm getting (if it ever arrives) is an 80GB drive - smallest I could lay my hands on new. Way bigger than I need but never mind. What I want to know is, when I install Ubuntu how will it partition that drive? If I go with the default and let it automatically partition - how many partitions will it create and what size will they be?  Would I be better to do it manually and if so, how would you recommend I arrange things?  If I do it that way which partition should I leave the bulk of my drive space in? This drive will only be used for Ubuntu so I might as well make use of the entire space.

Secondly, I have a home network of three machines. The host machine is on dial up (always on) and is connected to my machine and the kids machine via a switch, using ICS. When I get Ubuntu up and running, is there anything I  need to do with my network setup for it to recognise my machine when it's booted to Ubuntu? The other two machines run XP Home - mine will be dual booting Ubuntu and XP Home initially, with the intention of dropping XP once I've got the hang of Linux.

Many thanks for your help. I expect to be here a lot  ;-)

---

### Post by Kiwinote on 2006-01-10
If you install ubuntu in the default mode it will leave you with one 80gb partition and a 256mb swap partition, if you want more partitions(to dual-boot) you will need to partition it manually. A partition manager comes on the ubuntu-cd that you can use to partition the drive. I have a 20gb drive which I partitioned manually and am running ubuntu on 10gb, windows 98 on 9gb and a swap of 256mb.
As for the network, I'm not sure how that'll work out.
Good luck,
Kiwinote

---

### Post by GuitarFingers on 2006-01-10
A quick rundown on how to use ICS and Linux can be found here:

[http://www.annoyances.org/exec/show/ics_other]("http://www.annoyances.org/exec/show/ics_other")

Hope that helps,

Guitar Fingers

---

### Post by 504harry on 2006-01-10
[QUOTE=Kiwinote]If you install ubuntu in the default mode it will leave you with one 80gb partition, if you want 2 or more partitions you will need to partition it manually. A partition manager comes on the ubuntu-cd that you can use to partition the drive. I have a 10gb drive which I'm running ubuntu on and that's plenty, so you will need to decide yourself how big you want your partitions.
As for the network, I'm not sure how that'll work out.
Good luck,
Kiwinote[/QUOTE]

I'm more-or-less a newbie, but i understood the partition tool will (with some difficulty on yr part) create two partitions....one barely 500MB for swaps  and  79GB, or thereabouts for everything else.
However, I read that it is good practice to have a **third** partition for your files, but am uncertain how this manifests itself although it appears to make some sense.
My own 510 installation used a 130G stand-alone drive as 61 + 61 + (_tiny_) -don't know where the rest went, -best not to ask.
I messed it up by **not** having the internet connected at the time (so it seems?) and am soon to re-install(Grr.). The partitioning IMHO is my mental Barrier, otherwise I'd have stopped fafing abt ....and got on with it. 
/
For some reason Linux always expect Win to be there, but some suggest that crashes between OS's are twice as likely. As you have a decent-size HDD, give Ubuntu a try .......are you usiing a genuine Ububtu disc? or one of those wretched ISO types? 
Along with Partitioning, Ubuntu really needs to sort out ISO - it does my head in...... and progs like Nero6 just make it worse.
Oh! the darkened room becons.
Good luck, report back, pse.

---

### Post by J77 on 2006-01-10
Quick reply:

I had XP pro on my machine - 21.5 GB (ntfs) - with remaining 50ish GB free.

Stuck in the ubuntu DVD (install/live), booted from this and typed install at prompt.

Like you say, first thing is partitioning - did this manually as follows:

100 MB for '/boot' (type: primary, ext3)
10 GB for linux '/' (type: the other one - not primary, ext3)
4 GB (same as my memory) swap (change the dropdown from ext3 to find swap)
rest (type max) about 35 GB for data '/home' (type: the other one - not primary, ext3)

Worked fine - even the grub loader which makes the boot menu choice between linux and xp, I think... :smile:

---

### Post by Sef on 2006-01-11
For information on how to dual boot,  read this:  [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---


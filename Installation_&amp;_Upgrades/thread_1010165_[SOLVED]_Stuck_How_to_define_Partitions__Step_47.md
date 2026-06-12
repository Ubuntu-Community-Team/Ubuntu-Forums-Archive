---
title: "[SOLVED] Stuck: How to define Partitions ? Step 4/7"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by talofo on 2008-12-13
Hi all... I'm reading and reading... but found no solution. :(

I'm on step 4/7 of the instalation process.
I've choose manual because I need to keep the recovery HP Laptop partition intact.

I want to install Ubuntu and virtualize Windows.

I have something like this:

/dev/sda1 type: ext2 Mount Point: /boot Size: 512MB

/dev/sda5 swap Size: 4GB (I have 4 gb ram)

/dev/sda6 type: ext3 Mount Point: /  Size: 15GB (do I need a / partition?)

/dev/sda7 type: ext3 Mount Point: /home Size: 20GB

/dev/sda8 type: ext3 Mount Point:(nothing) Size: 200GB

Now the HP specific partitions:
/dev/sda2 type: fat32 Size: 1069MB

/dev/sda3 type: ntfs Size: 9GB



When I click forward, I get a warning:
No mount point is assigned for the ext3 file system in partition #8.

I want this to be the biggest partion, where all problems will be installed, for both, Ubuntu, and Windows when windows will be virtualized.




1) What kind of Mount Point should I have for sda8 ?


2) Is this partitioning ok?


Thanks a lot,
MEM

---

### Post by taurus on 2008-12-13
What do you plan to do with /dev/sda8?  You can mount it to /media/share for now and if you want to mount it somewhere else later, you just have to edit /etc/fstab.

And yes, you need a / partition even if you have a separate /boot & /home partitions.

---

### Post by albinootje on 2008-12-13
> I want this to be the biggest partion, where all problems will be 
> installed, for both, Ubuntu, and Windows when windows will be virtualized.

You meant "where all programs will be installed" ?
Then you want to give it /usr as mountpoint.

In general it makes more sense to give /usr about 15 Gb, and have much more space in /home 
( VirtualBox stores Virtual Machine inside /home/.VirtualBox/ )
But that's up to you of course.

---

### Post by talofo on 2008-12-13
> **taurus said:**
> What do you plan to do with /dev/sda8?  

Thanks. for the reply.

Well I want that partitions to have, downloaded stuff, movies, a lot of grafical stuff, musics, and A LOT of installed programs.


The problem is that: 
I need a lot of space for installing applications. But a lot of that space will need to be accesible by the windows virtualized. i.e. I need to install 4GB of Adobe Products that only run on windows. :(


Should we separate the programs install partitions from the data partitions? If so, what is the partition that will contain the installing programs? Is the / partition?



Regards,
MEM

---

### Post by taurus on 2008-12-13
Most of the apps that you install in Ubuntu will go into /usr/bin so basically you want / or at least /usr to have the majority of disk space.  However, movies and music will probably go into your $HOME (/home/<username>) so you want /home to have a large partition too.

---

### Post by luso13 on 2008-12-13
How to define Partitions ? 
I use GParted 0.3.5 (with Ubuntu 8.04). You can find it in Synaptic Package Manager.

This Partition editor is better then the one that comes with Vista. Good user interface with graphics showing the partitions in each HD.

---

### Post by albinootje on 2008-12-13
By the way, if you decide to use a / and a /usr and a /home partition, then you should realise that / can be much smaller than 15 Gb. 
1 Gb for / is already more than enough in that scenario.

---

### Post by talofo on 2008-12-13
Thanks albinootje and Taurus.

One last question...

We use /usr for multiuser system? In this case I will have only mysef, so adjusting the /home and / partitions will be ok, right?


Regards once again,
MEM

---

### Post by talofo on 2008-12-13
> **luso13 said:**
> How to define Partitions ? 
I use GParted 0.3.5 (with Ubuntu 8.04). You can find it in Synaptic Package Manager.

This Partition editor is better then the one that comes with Vista. Good user interface with graphics showing the partitions in each HD.

Thanks Luso. I've seen your post before. Well, I'm on ubuntu instalation setup, I don't know what partition system is these. It seams ok. (the only think I don't like, is that I'm unable to resize by dragging the mouse).

Regards,
MEM

---

### Post by talofo on 2008-12-13
Thanks a lot for all the replys, I have now a system like this:

(I've decided to take the usr advice, it seams more organized)

/sda1 ext2 /boot 512MB

/sda5 swap 4000MB

/sda6 ext2 / 1000MB

/sda7 ext3 /user 15000MB

/sda8 ext3 /home 210000MB

(the other HP partitions still the same think).


Let's go to step 5/7 YUPI!!!! :D:D:D:D:D

---

### Post by talofo on 2008-12-13
Ups. No it's not. I'm getting a warning telling me that some of the partions are to small.


Can this be because I define the / root partition to be smaller then the /user partition?


Thanks

---

### Post by taurus on 2008-12-13
To make life easy, I would just combine both / & /usr partitions into one partition--/.

I believe / is too small since everything else that is not installed to /usr will go to /: /var, /tmp, /root, /sbin, /etc, /lib, /sys, /bin, /dev, etc.

p.s.  By the way, it should be /usr, not /user.

---

### Post by albinootje on 2008-12-13
Cool! :)
But just making sure everything is OK, you probably meant /usr instead of /user in your last posting, no ?

---

### Post by talofo on 2008-12-13
Ok. Now it's solved. I have remove the /usr partition, and I've put only the /.

:) Step 5/7 :)

---

### Post by talofo on 2008-12-13
Yep. usr and not user. I'm so newbie!!! Yupiii for that to. :)

---


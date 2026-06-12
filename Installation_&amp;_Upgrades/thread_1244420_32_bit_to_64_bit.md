---
title: "32 bit to 64 bit"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by dave r on 2009-08-19
I have a 64 bit pc which, at the moment, has a 32 bit OS on it. I have separate partitions for the OS and Home. When I get round to installing the 64 bit system can I just go to manual partition, format the system partition to remove the old system and use that partition to install the 64 bit system on without touching the Home Partition? Or is it a bit more complicated than that?, do I have to do anything with the home partition or can I leave it alone? I have done a lot of research, both here and on the net,and have a rough idea of what I need to do, but any more precise information would be helpful.

---

### Post by Bucky Ball on 2009-08-19
I have been lead to believe that is correct and that is the way I would go about it myself. Manual partition, kill the old / and install on that. It may be pointing in all the wrong places, though, but that would be fixable I'd think. You may have to re-link some things in your old /home.

This is one I would like a definite answer on too as I am contemplating upgrading over christmas (yes, only four months away!). :)

---

### Post by VipX1 on 2009-08-19
I did it, I backed up my home partiton and just put it back on the home partition when the new install is done, I pasted my old home folder into the new home folder partiton and overwrite.. Had to be done as Root..
The new install is always going to make a new home folder no matter. That was the way I thought to get around it..

---

### Post by Bucky Ball on 2009-08-19
> **VipX1 said:**
> 
The new install is always going to make a new home folder no matter. 

Exactly what I was thinking. Now I remember this actually happened when I upgraded to 8.04 about a year ago and I fixed it but wouldn't have the foggiest idea how! I had two /home partitions and had to get rid of one and set the world to right again.

So your plan worked VipX1? No problems?

In Windows I run the OS on its own small partition specifically for this purpose. I can just kill it and re-install. I have noticed there is nothing quite as convenient (and safe) for this kind of upgrade or thinking in Ubuntu. It ain't that simple because of the fact a new install creates a new /home. Maybe some way of detecting an existing /home partition and asking if you'd like to keep it during partitioning? Would be great. ;-)

---

### Post by VastOne on 2009-08-19
> **dave r said:**
> I have a 64 bit pc which, at the moment, has a 32 bit OS on it. I have separate partitions for the OS and Home. When I get round to installing the 64 bit system can I just go to manual partition, format the system partition to remove the old system and use that partition to install the 64 bit system on without touching the Home Partition? Or is it a bit more complicated than that?, do I have to do anything with the home partition or can I leave it alone? I have done a lot of research, both here and on the net,and have a rough idea of what I need to do, but any more precise information would be helpful.

Since you have a \home partition, all your settings will be kept as long as you do not format that partition. The only two partitions that should be formatted are root and swap.  I export a list of my applications I use in Synaptic and can easily import them once the new build is done. 

I can blow away a sandbox test OS and reinstall a new kernel within 15 minutes with complete applications reestablished doing it this way.

---

### Post by VastOne on 2009-08-19
> **VipX1 said:**
> The new install is always going to make a new home folder no matter. That was the way I thought to get around it..


Not true if you have a partition already created that is home. You simply have to specify the right partition as \home when installing.

have a separate home partition is the most important piece of Ubuntu setup, IMHO

---

### Post by VastOne on 2009-08-19
> **Bucky Ball said:**
> Exactly what I was thinking. Now I remember this actually happened when I upgraded to 8.04 about a year ago and I fixed it but wouldn't have the foggiest idea how! I had two /home partitions and had to get rid of one and set the world to right again.

So your plan worked VipX1? No problems?

B-Ball, if I were you I would first create a separate \home partition and go from there. There is a very easy way of doing this at this site

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by dave r on 2009-08-19
> **VastOne said:**
> Not true if you have a partition already created that is home. You simply have to specify the right partition as \home when installing.

have a separate home partition is the most important piece of Ubuntu setup, IMHO

Thanks for all the information guys, VastOne if I already have a home partition will the installer just go with that partition or will it attempt to create another one? Will I have to specify the mount point for the home partition during the install to get it to use the existing one?

---

### Post by VipX1 on 2009-08-19
Can you confirm Vastone, It will not overwrite your /home folder in the paticular partition?
Therefore it doesn't make a new /home folder it just uses the existing /home as is..

That's a handy piece of info..

---

### Post by VastOne on 2009-08-19
> **dave r said:**
> Thanks for all the information guys, VastOne if I already have a home partition will the installer just go with that partition or will it attempt to create another one? Will I have to specify the mount point for the home partition during the install to get it to use the existing one?

When you install, you have to select the partition that is \home and edit it and make it \home again. It will not recreate it.  Make sure you do not format this one.

---

### Post by VastOne on 2009-08-19
> **VipX1 said:**
> Can you confirm Vastone, It will not overwrite your /home folder in the paticular partition?
Therefore it doesn't make a new /home folder it just uses the existing /home as is..

That's a handy piece of info..

Yes I can confirm this as long as you do not format your existing \home and select it when you are installing (edit partition and make it \home) you will be fine

---

### Post by Bucky Ball on 2009-08-19
> **VastOne said:**
> B-Ball, if I were you I would first create a separate \home partition and go from there. There is a very easy way of doing this at this site

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I have separate everything partitions for everything already, thanks. /home /music /vid etc. I am a stickler for doing it this way from the Windows days and totally agree with you. If the OS crashed, you didn't lose anything. Just killed it and reinstalled. A dead OS has not been a problem for a long time and I have NEVER used anything but manual partitioning. ;-)

---

### Post by VipX1 on 2009-08-19
Doesn't it format all newly assigned partitions when you hit install. Obviously not by what your saying VastOne. So your /home and dry Dave R.. 
Good question.

---

### Post by Bucky Ball on 2009-08-19
VastOne, you've done this? It didn't overwrite anything? It can acknowledge that it is an existing /home partition?

---

### Post by dave r on 2009-08-19
:D Thanks all, I now have a better understanding of what I am doing, The dirty deed is scheduled for Friday, I'll let you know how it went at the weekend

---

### Post by VastOne on 2009-08-19
> **Bucky Ball said:**
> VastOne, you've done this? It didn't overwrite anything? It can acknowledge that it is an existing /home partition?

YES a billion times yes...This is how I maintain everything I am working on so that I can test all new kernels and new releases

It does not overwrite your home settings...

So if you have say Exaile installed which keeps its database and settings in home, once you re-install Exaile all your settings will return, the same with Compiz and everything else you have preserved in \home

---

### Post by VastOne on 2009-08-19
> **VipX1 said:**
> Doesn't it format all newly assigned partitions when you hit install. Obviously not by what your saying VastOne. So your /home and dry Dave R.. 
Good question.

Installation will only format the partitions you tell it to format.  Even if you have Ubuntu installed already, and you do not tell it to format \Root and \Swap, it will ask you are you sure you want to keep the current \root because it will be overwritten. The safest way is to ONLY allow \Root and |Swap to be formatted

---

### Post by VastOne on 2009-08-19
> **dave r said:**
> :D Thanks all, I now have a better understanding of what I am doing, The dirty deed is scheduled for Friday, I'll let you know how it went at the weekend

If you have any questions as you go through this you can PM me at any time and I can try to assist.

---

### Post by dave r on 2009-08-19
> **VastOne said:**
> If you have any questions as you go through this you can PM me at any time and I can try to assist.

Thank you

---

### Post by Bucky Ball on 2009-08-19
Good. I'll try it when I install 9.04 eventually. By the way: /home not \home. ;-)

---

### Post by VastOne on 2009-08-20
> **Bucky Ball said:**
> Good. I'll try it when I install 9.04 eventually. By the way: /home not \home. ;-)

indeed...thanks tired and old now, no excuse...lol

---

### Post by Bucky Ball on 2009-08-20
lol

---

### Post by dave r on 2009-08-20
OK I did the deed tonight. Upgraded to 64 bit nice and smooth no problems, it went as smooth as silk with no lost data. But I have hit a snag. There are three users on this computer, the home files are there and intact but they cannot log onto them. I need to restore their ability to log on, any ideas?

---

### Post by dave r on 2009-08-21
Any ideas guys?

---

### Post by dave r on 2009-08-21
Sorted it. started a session as root, deleted the folders, created new users, and restored data from backups

---

### Post by Bucky Ball on 2009-08-21
Now why didn't I think of that? lol Good one. :)

---


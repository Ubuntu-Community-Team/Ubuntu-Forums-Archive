---
title: "how to install on a hardrive in a special way?"
date: 2008-09-18
forum: Hardware
---

### Post by m9365428 on 2008-09-18
Hey i have an 80 gig and a 160 gig hdd and i want to set up an installation where i have the os installed on the 80 gig drive and all of my data on the 160 gig in a  universal partition. 
I don't even know if that kind of setup exist or what it is called so if you know or have an idea what it is called plz let me know.
I want to do this with all os's that i install without the need to partition away my data to each os and just have one partition with all my data on it.

Thanks for your time 
M

---

### Post by unca.paka on 2008-09-18
Youll have to manually create the partitions on the drives, the ubuntu installer will give you this option, just choose to manually change the partitions. 
Just set the base system partitions on the 80gb drive(/, /swap, /boot), then you can throw your /home folder on the 160

---

### Post by m9365428 on 2008-09-18
> **unca.paka said:**
> Youll have to manually create the partitions on the drives, the ubuntu installer will give you this option, just choose to manually change the partitions. 
Just set the base system partitions on the 80gb drive(/, /swap, /boot), then you can throw your /home folder on the 160

thanks for the reply but i think there is a particular drive configuration like RAID or something. I know that RAID is not what i'm looking for but i don't know what to call it.

M

---

### Post by lswb on 2008-09-18
Your idea is good. There are several variations. What I do is have a /data partition, then symlink to it from the user home directory of each OS. On /data for example I have /data/music directory that is read/write accessible from any running OS. You will have to mount the partition in each OS, in linux this is typically done at boot with a line in /etc/fstab.

If you format the /data partition as ext3 or similar you can use permissions on different directories to allow or restrict access by different users however you'd like. OTOH, if you are running windows on the same computer you may want to partition /data as vfat or ntfs. vfat has the advantage that pretty much any OS can access it without problems, but it has no native permission capabilities.

---

### Post by m9365428 on 2008-09-18
> **lswb said:**
> Your idea is good. There are several variations. What I do is have a /data partition, then symlink to it from the user home directory of each OS. On /data for example I have /data/music directory that is read/write accessible from any running OS. You will have to mount the partition in each OS, in linux this is typically done at boot with a line in /etc/fstab.

If you format the /data partition as ext3 or similar you can use permissions on different directories to allow or restrict access by different users however you'd like. OTOH, if you are running windows on the same computer you may want to partition /data as vfat or ntfs. vfat has the advantage that pretty much any OS can access it without problems, but it has no native permission capabilities.
okay cool do you know of any websites that do a how to for the top linux distros and windows xp(forced to use for school programs) 
M

---

### Post by lswb on 2008-09-19
> **m9365428 said:**
> okay cool do you know of any websites that do a how to for the top linux distros and windows xp(forced to use for school programs) 
M

Here's one that's pretty good:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
and one of the links on the same site:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by m9365428 on 2008-09-19
> **lswb said:**
> Here's one that's pretty good:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
and one of the links on the same site:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Okay thanks for the post but I'm still a little lost. I think I can see where the first page is going but it looks complected.
Just to verify I want my os's on one hdd and all my data on a second hdd. I also want to be able to access all of the data on the second hdd from any of the installed os's wether they be linux win xp or otherwise.
Dose that kind of setup even have a name?

M

---

### Post by mick222 on 2008-09-19
I'm no expert but don't try to share your home partition between distro's .
I tried that with Ubuntu and suse and it wrecked my home paartition.
create a /data partition on the 160 gb drive with gparted and use this instead of home for your music etc.You might have to edit fstab so check out posts related to it. hopefully someone more knowledgeable will come along and explain.

---

### Post by m9365428 on 2008-09-19
> **mick222 said:**
> I'm no expert but don't try to share your home partition between distro's .
I tried that with Ubuntu and suse and it wrecked my home paartition.
create a /data partition on the 160 gb drive with gparted and use this instead of home for your music etc.You might have to edit fstab so check out posts related to it. hopefully someone more knowledgeable will come along and explain.

Ok but my question is would I be able to install all of my software in a "programs" folder instead of in the os partition on the small hdd. and could windows read that data partition on the second hdd.
I'm trying not to have to separate my 160 gig hdd into small chunks for each os's data and save files.
M

---

### Post by lswb on 2008-09-19
> **m9365428 said:**
> Ok but my question is would I be able to install all of my software in a "programs" folder instead of in the os partition on the small hdd. and could windows read that data partition on the second hdd.
I'm trying not to have to separate my 160 gig hdd into small chunks for each os's data and save files.
M


These are my opinions and I'm sticking by them :) :

If by software you mean executable programs, the general answer is no. There's plenty of room for Windows XP and several linux distributions on an 80GB hard drive, I wouldn't worry about that too much. (I have a laptop with XP, 2 linux distros, a 20GB data partition and an empty 10GB partition all on a single 80GB drive) 

OTOH, data files like music, pictures, documents, movies, etc are easily shared between different OS.

You have a few choices for formatting the data partition so it is accessible by windows:

vfat
pros: windows and most every other OS can read & write to vfat.
cons: Doesn't use linux/unix style permissions

ntfs:
pros: windows can read/write, most linux distros can read/write nowadays
cons: Doesn't use linux/unix style permissions, occasional problems can prevent linux access. (So I've read anyway)

ext3:
pros: Uses linux/unix permissions.
cons: needs special driver for windows to access. 

I don't know anything about the windows driver for ext3 filesystems, maybe someone who has tried it can comment.

It's not hard to set up but there are lots of variations and ramifications that are difficult to cover in a forum post. I suggest doing some reading & research, then just try out what you consider best suits your needs. You have plenty of space to play with and can always change things til you get it just like you want it. Just remember to make backups whenever you do anything like shrink/expand/move partitions.

---

### Post by m9365428 on 2008-09-20
Okay thanks for the list of how the partition types are used and accessed in the different os's. 
Unfortunately my plans have changed. I will be forced to run Vista and not XP on the dual boot and the hdd is going to be another 160gig because it is cheaper.
I'm still going to try and set this thing up though. all this really means is that I will have more room to install programs in the windows partition instead on in the universal partition. Although I may just set up an OS on each drive now.

M

---


---
title: "If a separate home partition is such a good idea ..."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by b9k9kiwi on 2009-10-30
... why isn't installing with a separate home partition an easy option when undertaking an Ubuntu fresh install?

I have two Ubuntu PCs - one is just a standby machine should my main one die on me.  I have installed Jaunty twice on the standby (fresh each time), the second occasion because the first install was zapped by an attempt by me to create a separate home partition following the 'how to' available in Ubuntu Forums.

I rather expected 'would you like to create a separate home partition' to be an option when I installed Karmic fresh onto the No2 PC as there seems to be relatively widespread enthusiasm for it.  You can create partitions manually during install I know, but I recall the process being somewhat opaque as to partition location and relative size.

I will have to install Karmic fresh on my No1 as the upgrade from Hardy to Jaunty didn't go so well (I lost the ability the share folders across the network, for example, and have not been able to reinstate sharing), and a separate home partition would seem to be a prudent step to take if all advice is accepted.

Maybe it isn't such a good idea, however, as it remains such a tricky option to instigate.

---

### Post by morphodone on 2009-10-30
It is a good idea to have separate partitions... this way you can always install a fresh copy of ubuntu and the /home partition remains intact with all your user files.

My drive has 3 paritions
/
swap
/home

And as for the size:
/ - max of 10 GB
swap - usually 1 GB
/home - is the remainder of the drive

I always use the alternate installer disc and setup the partitions that way.
You just have to setup your /home parition - and DO NOT FORMAT IT.

---

### Post by howefield on 2009-10-30
> **b9k9kiwi said:**
> You can create partitions manually during install I know, but I recall the process being somewhat opaque as to partition location and relative size.

The second half of the Ubuntu Partitioning video here might make it a little clearer. The video is around 10 minutes long.

[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

---

### Post by RTrev on 2009-10-30
I've never used a distinct /home partition, because it always seemed to me that it made more sense to only make copies of the folders for the applications I care about, and allow the system to upgrade the rest of /home as needed.  For example, if a new version of Gnome wants to put some new files there during install of a new version, why not let it?

At one point I had multiple distros installed, so I would use symbolic links in my home directory to point to the real directories which were out on another drive.

When I decided to stick with straight Ubuntu, I just make a note to copy those directories from backup after doing a clean install of a new version.  So I might copy the directories .mozilla, .gftp, .pan2, and so on, from the previous install.  But everything else in /home gets created new with each new clean install.

Maybe I'm all wet about this, but it seems like I'm getting a cleaner install that way.

---

### Post by morphodone on 2009-10-30
> **RTrev said:**
> So I might copy the directories .mozilla, .gftp, .pan2, and so on, from the previous install.  But everything else in /home gets created new with each new clean install.

Maybe I'm all wet about this, but it seems like I'm getting a cleaner install that way.

That's a good point... I've been using the same /home since probably warty!
From time to time I go and clean it out.  All of those hidden folders and files build up.

I just don't like the thought of accidentally fresh installing over all my music, pictures, tax documents, etc...  What do you do with all that stuff when you install?

---

### Post by RTrev on 2009-10-30
> **morphodone said:**
> That's a good point... I've been using the same /home since probably warty!
From time to time I go and clean it out.  All of those hidden folders and files build up.

I just don't like the thought of accidentally fresh installing over all my music, pictures, tax documents, etc...  What do you do with all that stuff when you install?

All of my data resides on other physical hard drives, so as part of my install of a fresh version of Ubuntu I create mount points in /mnt and create symbolic links to them in my /home directory.  Then I tweak /etc/fstab to mount those other drives, and there's my data.

I always mount those drives the same way, so the programs know where to find their data from the config files in their directories which I've restored into my new /home/bob directory.

Make sense?  Despite my lousy explanatory skills? <g>

---

### Post by macogw on 2009-10-30
> **RTrev said:**
> I've never used a distinct /home partition, because it always seemed to me that it made more sense to only make copies of the folders for the applications I care about, and allow the system to upgrade the rest of /home as needed.  For example, if a new version of Gnome wants to put some new files there during install of a new version, why not let it?
They'll write the files anyway.  Per-user config files are written on a program's first run.

Also:
I think everybody forgets the part where if you choose Manual and then select the partition that was / before and tell it to NOT format....it'll keep your /home directory.

---

### Post by morphodone on 2009-10-30
> **RTrev said:**
> All of my data resides on other physical hard drives, so as part of my install of a fresh version of Ubuntu I create mount points in /mnt and create symbolic links to them in my /home directory.  Then I tweak /etc/fstab to mount those other drives, and there's my data.

I always mount those drives the same way, so the programs know where to find their data from the config files in their directories which I've restored into my new /home/bob directory.

Make sense?  Despite my lousy explanatory skills? <g>

I somewhat get what you are saying... I think I'm just too lazy for all that.:p

---

### Post by morphodone on 2009-10-30
> **macogw said:**
> Also:
I think everybody forgets the part where if you choose Manual and then select the partition that was / before and tell it to NOT format....it'll keep your /home directory.

How does that work?  If / is not formatted then what happens.  Seems like a lot of stuff would still be there that doesn't need to be.

If I format / then I know it's definitely fresh.

---

### Post by RTrev on 2009-10-30
> **macogw said:**
> They'll write the files anyway.  Per-user config files are written on a program's first run.

Also:
I think everybody forgets the part where if you choose Manual and then select the partition that was / before and tell it to NOT format....it'll keep your /home directory.

So I'm not gaining anything by doing it the way I described?  Oh well.  Live and learn. ;)

The only thing, though, for this install of Karmic, if I used your approach I'd still have an ext3 system instead of an ext4 one, no?

---

### Post by macogw on 2009-10-30
> **RTrev said:**
> 
The only thing, though, for this install of Karmic, if I used your approach I'd still have an ext3 system instead of an ext4 one, no?

Right. But I'm a little leery of ext4 anyway.  A few people (including me) have hit corruption issues on very large files on ext4 in Karmic.

---

### Post by lovinglinux on 2009-10-31
> **b9k9kiwi said:**
> I rather expected 'would you like to create a separate home partition' to be an option when I installed Karmic fresh onto the No2 PC as there seems to be relatively widespread enthusiasm for it.

openSuse does that.

You could create a new suggestion at [Ubuntu Brainstorm](http://brainstorm.ubuntu.com/).

---


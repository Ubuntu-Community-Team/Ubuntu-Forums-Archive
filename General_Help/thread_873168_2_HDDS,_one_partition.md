---
title: "2 HDDS, one partition?"
date: 2008-07-28
forum: General Help
---

### Post by gnomey on 2008-07-28
Hey,

Is it possible to format 2 HDDs as one partiton?

If not is it possible to install software on a different HDD then the one the distro is installed on?

---

### Post by sdennie on 2008-07-28
It sounds like you want to use either LVM or RAID.  If you google for either of those things, you should find many guides that may be applicable to you.

---

### Post by gnomey on 2008-07-28
What I have is my Eeepc.

it has a built in SSD (solid state disk) with only 4GB space,however I have an 8GB SD card as well.

Could I install software on the 8GB?

I was thinking of making one partition but that doesnt look so good now, any one shed any light on this?

---

### Post by jonian_g on 2008-07-28
Check this thread, it's similar:

[http://ubuntuforums.org/showthread.php?t=871313](http://ubuntuforums.org/showthread.php?t=871313)

info about Eeepc and ubuntu here:

[http://www.ubuntu-eee.com/index.php5?title=User_Guides](http://www.ubuntu-eee.com/index.php5?title=User_Guides)

Download ubuntu ready foe Eeepc Here:

[http://www.ubuntu-eee.com/index.php5?title=Get_Ubuntu_Eee](http://www.ubuntu-eee.com/index.php5?title=Get_Ubuntu_Eee)

---

### Post by derrick81787 on 2008-07-29
> **gnomey said:**
> Hey,

Is it possible to format 2 HDDs as one partiton?

You can look into something like unionfs to mount the to drives at two different mount points and then combine them so that they *appear* to be one partition/mount point. [http://en.wikipedia.org/wiki/UnionFS](http://en.wikipedia.org/wiki/UnionFS)

> **gnomey said:**
> If not is it possible to install software on a different HDD then the one the distro is installed on?

I answered a question almost exactly like this earlier today.  Basically, yes you can, thanks to the fact that you can mount a partition literally anywhere you want.  Take a look at my post here [http://ubuntuforums.org/showpost.php?p=5481872&postcount=8](http://ubuntuforums.org/showpost.php?p=5481872&postcount=8)

---


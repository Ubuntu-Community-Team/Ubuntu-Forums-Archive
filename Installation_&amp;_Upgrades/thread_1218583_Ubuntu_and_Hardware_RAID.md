---
title: "Ubuntu and Hardware RAID"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by phibit on 2009-07-20
Hi,

I recently bought 2x500 GB hard drives, and I would like to set them up in a hardware RAID 0 configuration, but I'm not sure how well this is supported in Ubuntu.

My understanding is that, to install Ubuntu on a RAID array, you need to use the alternate install CD, but apart from that I have zero knowledge.

Does anybody have some experience or knowledge with Ubuntu and hardware RAID arrays?

Or, does anybody have any positive experiences with Ubuntu and software RAID arrays?

Any advice would be very appreciated!

Also, on a related note, I'd be really interested to hear from someone who had actually run a RAID 0 or 1 configuration with Ubuntu, and how much of a performance difference they noticed, if any.

Thanks a lot!

---

### Post by phibit on 2009-07-21
bump!

---

### Post by bacil on 2009-07-21
Hi,

here is catch i am runing ubuntu on old compaq server with HW raid it took me good week to get drivers for that particular raid. so if youa re planning to use raid please have look for your hw support. (i have to admit that my one is really old hw so that may hava caused it). 

as for preformance there is no overhead on os since all raid operations are handled on selarate chip on raid card. thats difference from sw raid where those are handeld by os and creating some overhead.

Any questions ... just ask :-)

---

### Post by phibit on 2009-07-21
Hey! Thanks a lot for the reply! I'm glad to to hear there is no noticeable overhead for hardware raid, and you raise a valid point that I should check if my RAID controller is supported.

The RAID controller I'll be using is the one that's on my XFX nForce 680i motherboard. I'm trying to look up the specs now, but all I seem to be able to find out is that it's a "NVIDIA MediaShieldTM RAID", which I'm fairly sure is just a branding of RAID, and not the controller model.

After some research, I've discovered that the "RAID" controller on my motherboard is actually a "fakeRAID" device, and as I understand from reading various articles, this is just a poor-man's emulation of hardware RAID, where the CPU does most of the work. Additionally, it seems that fakeRAID is not well supported in Ubuntu.

With this in mind, do you think I would be better off just using an Ubuntu software RAID?

---

### Post by bacil on 2009-07-21
I would stick to sw raid for now i guess since you will have better control from OS on what and how it is replicated you can play with things like delayed flush and others really depending on your preferences. 

cpu degradation is to be expected, but again it will depend on type of IO you are likely to have. if your application is write intensive degradation will be higher if you get random writes etc.

what application you are planing to use ? and what IO's do you expect ?

---

### Post by phibit on 2009-07-21
Mmmmmmmmmmm good question. The machine is my desktop (so I use IDEs, firefox etc...), that I also use as a webserver/fileserver/sqlserver/subversion repo.

It doesn't get huge amounts of traffic on the server side, so the IO load isn't too intense.

Another question. I'm still deciding between RAID 0 and RAID 1... The idea is I want at least SOME performance gains from this RAID array. So my next question is... Will mirroring at least give me READ performance gains? And will it really slow down my write speeds?

If I knew that I would get just a small performance gain from mirroring, I would choose that, for the data security bonus.

---

### Post by bacil on 2009-07-21
well then i dont think you should worry about performance degradation in wht you running unless  your sql is real time relational database serving hundreds of request at the time :-)

on your mirroring you will gain some speed based on prefetch algorithm used (that is what filesystem) you going to use on your device as well as how are you planning to do  actual mirorring in OS.

in old days when i used solstice on solaris it had no performance impact whatsoever since it only did write each io 2wice and red from one disk (alwas the first one in mirror).

So it will all depend what you planning to use. if comercial vxfs with all nice things that it can do or some free product.

---

### Post by phibit on 2009-07-21
Probably I will be using ext4 filesystem! Sounds good! Thanks for all the help!

---

### Post by bacil on 2009-07-21
my pleasure, Let me know how it goes :-)

---

### Post by phibit on 2009-07-22
I've been looking into it, and it sounds like fakeRAID in intrepid/jaunty actually isn't such a bad idea.

Does anybody have any experience with setting up a fakeRAID array with Ubuntu (and maybe a dualboot with windows?).

Thanks!

---

### Post by realzippy on 2009-07-22
HI!
Forget the fakeraid.Set up a softwareraid.
Have a look please:

[http://ubuntuforums.org/showthread.php?t=1212123](http://ubuntuforums.org/showthread.php?t=1212123)

Greetz

---

### Post by phibit on 2009-07-22
Sounds like a good plan! Thanks for the reply. Yeah, it looks like fakeRAID + linux is a recipe for problems.

So now the question is... should I RAID 0 or RAID 1? I'm leaning towards mirroring, because my array will have all my important user data. But I am also really hoping for some measurable performance boost.

Is it true that mirroring gives a READ performance boost?  Seems to me like that would make sense, seeing as it can technically read chunks from each drive.

Also, I have two 500GB drives, but I am not sure if they have the same amount of cache? It's possible that one has 16MB and one has 32MB. Is this going to be a big issue?

Thanks!

---

### Post by ronparent on 2009-07-23
If you want to retain compatibility with windows, you are stuck with fakeraid. Software raid won't cut it in that case.

Raid0 is a stripped array and gives you, reportedly, a significant boost in read/write speeds. But failure of either drive effectively wipes out all data on the raid0. Raid1 (mirroring) leaves the data intact on one drive if the other one is wiped out. But the performance gain is marginal. If your data is important to you, you absolutely need a backup strategy for a raid0 setup, It would also be advisable with the raid1 but not essential. Any difference between the drives may cost you some performance penalty. Have fun.

---

### Post by bacil on 2009-07-23
+1 ON THAT

If you use sw raid your windows will not be aware of it and you will not be able to use your data there.

Raid 1 for protection but no performance gain.but it will depend on technology used.

---


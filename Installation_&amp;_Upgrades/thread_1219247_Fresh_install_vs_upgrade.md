---
title: "Fresh install vs upgrade"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by bcn17 on 2009-07-21
I have been using ubuntu since 7.10 and have religiously reinstalled my root and home partitions the day ubuntu has come out every 6 months. The idea of a fresh install seemed/felt "cleaner." Is this necessary at all. What are the potential differences with the exception of file system format. (ext3 vs 4)  When 9.10 comes around should I just go for the upgrade and see how it goes? 

Furthermore, If I were to just do a fresh install over the root partition and leave my home partition would the two partitions integrate smoothly or would I still have to reinstall things like thunderbird via aptitude. 

And, if I installed applications again would they automatically synch up with the files they were using previously?

I mean, its not that hard to back up a home partition considering I keep all of my data thats not in Desktop on a data partition anyways. It's just kinda of a pain in the *** to screw with thunderbird profile manager etc.

---

### Post by Shpongle on 2009-07-21
when i upgraded from intripid to jaunty , it was just like a normal update, i was lucky that everything worked others have had problems, so id wait for a while and see how others get on or dl a live cd , and see how it runs on your system, all your setting are kept intact too it just updates the system like a normal upgrade, if you were gonna do a fresh install anyway, you mite aswell try update you got nothing to lose

---

### Post by cadkins on 2009-07-21
I've always done the same as bcn17.  But I have a question up the upgrade from Ibex to Jaunty.  

DillByrne : did you partition your home directory or do you just use the default Ubuntu install?  I have not partitioned my home directory separate from the rest of the directories (root, swapt,etc...).  I was told that this would probably cause problems.

I have done the "Upgrade" from Synaptic before and lost X and had to end up reinstalling anyway.

---

### Post by merlinus on 2009-07-21
> 
I have not partitioned my home directory separate from the rest of the directories (root, swapt,etc...). I was told that this would probably cause problems.
Don't know where you read this, but having a separate /home partition makes reinstalling and/or installing a new version much, much easier, as all of your application configurations and settings, email, bookmarks and such remain intact.

You simply choose to use that partition, but not to format it.

---

### Post by mudcat on 2009-07-21
I personally prefer a fresh install, but there's nothing wrong with an upgrade

---

### Post by cadkins on 2009-07-21
> **merlinus said:**
> Don't know where you read this, but ...


I typed that wrong.  What I meant was that by trying to upgrade with home *not* partitioned, I would run into a lot of problems.  :)

---

### Post by merlinus on 2009-07-21
OK.  You can create a separate home partition by following these instructions:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by philcamlin on 2009-07-21
> **mudcat said:**
> I personally prefer a fresh install, but there's nothing wrong with an upgrade

+1 fresh also has less issues

---

### Post by bcn17 on 2009-07-22
> **merlinus said:**
> OK.  You can create a separate home partition by following these instructions:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


I'm sure this would work fine, however ubuntu installs easy/fast enough that it seems it would just be easier to reinstall and make a home partition then. much less room for error and probably close to as fast as long as you have a data partition or an external HD for backup. 

But, if you are feeling like getting your hands dirty then go for it. That's half the fun with linux. :D

---


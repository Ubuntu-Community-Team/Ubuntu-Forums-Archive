---
title: "No Free Space -- Help!!"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by thisnamestoolong on 2009-04-28
Ok first off -- full disclosure here -- I am a complete Linux n00b. I installed Ubuntu 9.04 x64 yesterday to dual boot with Vista (also x64). I departitioned 30 GB before the install, as that is all I will need for free space. I got Ubuntu up and running, then attempted to use Firefox to download my display drivers and to my dismay was told that I have no free space. It appears that the Ubuntu install created a new partition EXACTLY the size of the install to install itself on and refuses to address any other hard disk space. Again, I am sure that I am making some boneheaded, n00b mistake, but I would really appreciate help in transitioning away from the tyranny of m$ once and for all, I had a really hard time going back to Vista again last night after seeing how peppy my computer can be when it's not bogged down by that bloated piece of crapware that they call an O/S. Thanks!

---

### Post by thisnamestoolong on 2009-04-28
Oh, and I can see the free space and even mount it as a volume, but it is still not helping. I can't even download to anywhere else because there is not enough free space to create the temp file to start the download.

---

### Post by dLeon on 2009-04-28
It will not an easy answers.
Answer1:
But, you need to know a bit about partition and repartition to do a manual partition setup in Ubuntu installation. I never use the automatic partition suggestion mode in Ubuntu setup. It more confusing than the manual setup and seems buggy, at least for me.

Answer2:
You can download Gparted iso or systemrescue.iso cd (contain Gparted) to do partition resize. I forgot their web address, but their famous try Googling. Still, you need to understand how to repartition though.

---

### Post by drs305 on 2009-04-28
I recently wrote a HOWTO on finding "lost" free space. You can view it here: [HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

However, in this case, as you guessed, it is probably a partitioning problem so if you could post the results of the following command we can see what you ended up with:
```

df -Th

```

If you haven't yet opened a terminal and don't know how: Applications, Accessories, Terminal would be the most familiar way. ;-)

---

### Post by eyescovered on 2009-04-28
> **drs305 said:**
> I recently wrote a HOWTO on finding "lost" free space. You can view it here: [HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

However, in this case, as you guessed, it is probably a partitioning problem so if you could post the results of the following command we can see what you ended up with:
```

df -Th

```If you haven't yet opened a terminal and don't know how: Applications, Accessories, Terminal would be the most familiar way. ;-)

installed without checking disc partitions so i thought i was screwed, just tried GParted and it worked fine and now i have more room! thanks!

---


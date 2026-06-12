---
title: "One Ubuntu, Two Partitions......"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by Odin8778 on 2009-06-26
Alrighty, first time newbie here, but not a big question.

I just installed Ubuntu 9.04 on my friend's laptop, after him having XP for a number of years.

He's used to installing XP on one partition and saving his files to another, on account of having XP crash sometimes.

Is it practical to do this with Ubuntu? I mean, when one installs something with Add/Remove Programs in Ubuntu, where does it actually install to? And if one were to set up a partition, would it indeed be in ext3 format?

---

### Post by Bartender on 2009-06-26
Just look up threads that talk about "/home"

There are thousands of 'em.  And, yes, you would set up the separate partition as ext3 or ext4.

---

### Post by mikewhatever on 2009-06-26
Personally, I like having a system partition, a home one and a storage. How practical it is depends on what suits your needs. Unlike Ubuntu, XP doesn't come on a live cd which can be used to access the files if the installed OS doesn't boot.
Programs are installed to the system partition.
A file system can be chosen, but ext3 is the default for now.

---

### Post by Odin8778 on 2009-06-26
Thanks for the advice :o

---

### Post by raymondh on 2009-06-26
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

Good luck.

---


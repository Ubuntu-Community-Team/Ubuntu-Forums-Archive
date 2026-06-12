---
title: "Partitions on a 64GB SSD Dell Mini 9"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by noibs on 2009-02-18
I'm going to put Ubuntu 8.10 (i386) on a Dell Mini 9 that has 2GB of RAM and a 64GB SSD drive.  I'm buying it from a Windows person who decided that Vista on a Dell Mini 9 wasn't that great.

1. Should I use a swap partition?  If so, should be it be 4GB?  Larger?  With 2GB of RAM and the apps I'll be using, it's doubtful that anything will be swapped out of RAM.

2. My plan at this time is to use 3 partitions--system/apps; home; and (possibly) swap.  I'll be using Open Office, GIMP, Firefox, some kind of email client, a handful of games (not many), some multimedia apps and various utilities.  How large should the partition holding the system and applications be?

If it makes any difference, I'm coming from a Mac background, although I have put various Debian, Ubuntu and YDL distributions on several Mac notebook computers in the past 3 years--just to learn about Linux.

Thanks.

---

### Post by InspiredIndividual on 2009-02-18
I think this link gives quite good information: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

You can find a more comprehensive HOWTO here: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Apart from the first link, it might be useful to read the parts on an extended partition in the comprehensive HOWTO. I didn't read the comprehensive HOWTO before partitioning my harddrive when I first switched from Windows to Ubuntu, and I rued it afterwards. Some parts that might be especially useful:
> 
swap size

       1. RAM < 1 Gb swap = RAM X2.
       2. RAM > 1 Gb swap = 2 Gb

So I'd go for a 2 GB swap if I were you.

> 
/ = root min size 5 GB (Yes, I know you can go smaller if needed), 15-20 Gb may be better if you have the HD space.

This depends on how you're going to use your computer. If you're planning to download many media files (video, music and stuff) then you may need all the space you can grap on your home partition. For me personally, I don't have many media, but I do have some very large and heavy applications. I started with a 10 GB root partition, but I had to repartition because I ran out of space very quickly (now, I've used some 12 GB on my root partition).

---

### Post by noibs on 2009-02-19
Thanks for the excellent links and good advice.

---

### Post by InspiredIndividual on 2009-02-19
> **noibs said:**
> Thanks for the excellent links and good advice.

Anytime! Always happy to help.

---


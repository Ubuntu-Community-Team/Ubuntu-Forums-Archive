---
title: "Partitioning"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by Cyfr on 2005-12-28
Hello, im going to do a complete reinstall of Ubuntu and want to create partitions so that I dont lose everything next time I reinstall, and basicly want to know what are the recommended partitions and sizes for a 160GB hard drive?

I'm a total newb so please explain as much as possible.. as far as i've read I think I need a / swap boot and /home partition, but really don't know how much space each of these should have.

Ps. I have 1gig of ram as I think you'll need to know that for the swap partition space!

Also, i've no idea what 'type' each partition needs to be so as I say please can you try and put as much detail as possible thankyou!! :)

---

### Post by infoseeker on 2005-12-28
I installed Gentoo Linux a few weeks back and their installation guide makes this quite clear.

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4)

---

### Post by psusi on 2005-12-28
That guide only recomends 32 MB for /boot.  That is not really enough.  You should go for 50-100 MB for /boot, make swap as large as the amount of ram you have, and / should be at least 5-10 GB, preferably 15-20.  Use up the rest for /home.

---

### Post by MrCheese on 2005-12-28
I'd go for something like this with a 160Mb disk to play with - 

/boot - 100Mb (extremely generous, plenty of room for kernel upgrades !)
/ (root) 1Gb
/swap 1Gb 
/var 2Gb (again, plenty of space for the apt cache)
/usr 4Gb
/home - the rest

Personally I make /boot an ext3 fs, the rest are Reiserfs (except swap of course). 

I also used to have an /opt for playing with non-standard stuff but I usually do all that kind of thing in /home now.

---

### Post by psusi on 2005-12-28
Why seperate out /var and /usr?  It makes it simpler to just leave them in / and when you reinstall, everything goes there and you just mount your old data in /home.  

I use reiserfs too, and one of these days I'm going to experiment with reiser4, but ext3 seems to be the safer/simpler thing so unless you want to experiment with other filesystems, it's a good default.

---


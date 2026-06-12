---
title: "Can't change SD card label"
date: 2012-12-26
forum: Hardware
---

### Post by Cadeyrn on 2012-12-26
I got a new class 10 8GB SanDisk, and the first thing I did was set a label to my new card: Death Card. Unfortunately, I made a typo and hit enter, and so now it carries the horrendously stupid title Death Carda. No matter how much I relabel or even reformat the card, no matter how much I eject it or put it into different computers, it simply refuses to let me change the label again. I've even tried running dosfslabel in the terminal (which returned no errors).

I have some experience with newer versions of Ubuntu, especially when running KDE, sometimes sticking to the first label it saw a device have, and somehow rendering it completely unchangeable until I find some random Mac out there in the world and rename it there. I have no idea how this problem works or if what I'm saying sounds like impossible nonsense, but I swear I see my installations of Ubuntu do it to my flash drives all the time.

By the way, the read-only lock is not on. Please don't ask about that.

---

### Post by oldfred on 2012-12-26
I like to use Disk Utility to change labels. It seems to work with all partition types. 

I also like to not include spaces in labels. Then it is easier to work with in Linux. I prefer CamelCase or under_score or justonelonglabel, but some partition types only allow 12 characters. FAT formated partitions often only allow all caps.

---


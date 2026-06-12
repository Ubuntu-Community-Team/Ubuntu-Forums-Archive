---
title: "Paritions and Swap"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by nmaster on 2009-06-14
I am planning on installing Jaunty sometime soon.  I plan on leaving my HP recovery partition (currently the D drive).  On the rest of the hard disk (C drive) I was going to put an extended partition with a logical partition for root and another logical partition for swap.  I know some people like having home as a separate partition, but for the sake of simplicity I don't (plus psychocats.net shows how to do this afterwards if I change my mind).

Question 1:
If I have 3 GB of RAM and am planning on using 64-bit Ubuntu, how much swap space should I have?  I don't game at all.  The most intensive thing I use is Matlab.

Question 2:
Does it matter where I put the swap?  To the left of root?  To the right of root? (Sorry if that is a really stupid question.)

Question 3:
Should I just make primary partitions for both swap and root?  I know that the limit is 4 primary partions and I therefore am able to, but I'm not sure why I would want to or wouldn't want to.

---

### Post by merlinus on 2009-06-14
I like to place /swap at the very end of the hdd, and it is 1.4G. 

If you will not be partitioning / ever, then all primary will not be a problem.  But if you can see a possibility down the road, then make them all logical, as this offers much more latitude in terms of changes.

There is no downside either.

---

### Post by nmaster on 2009-06-14
> **merlinus said:**
> I like to place /swap at the very end of the hdd, and it is 1.4G.

Can you explain why at the very end?  Also, how much RAM do you have? This help site recommends have a swap that is 1-2 times the amount of RAM.  [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by raymondh on 2009-06-14
> **neal.m.master said:**
> Can you explain why at the very end?  Also, how much RAM do you have? This help site recommends have a swap that is 1-2 times the amount of RAM.  [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

1-2X RAM for swap does make sense if you have a low-RAM situation as swap is used as storage for suspend ops.  But, with your set-up of 3GB, I think 1-1.5GB swap should be more than enough.  I think of SWAP as a spillover-catch basin for RAM.  

From what I read and understood ...during the olden times in low ram situations.... where to put SWAP so it can be most advantageous will depend on the number of disks/plates you have.  SWAP is there so it could be accessed soonest.  Remmeber that HD's have to move their heads to write, read and access data and that moving the head takes time.  The goal, thence, is to have the least time wasted when the heads have to move to access, read or write data.

With multiple disks, putting SWAP in front sectors is OK because one head can write in to swap while the other head can access and read other data, etc. (i.e. parallelization of disks').  Now, with a single disk, theoretically is is better to have SWAP in the center sector of the HD because the head will only have to travel half the distance from center to border as opposed to a full distance from border to border .... half the distance = less time wasted = faster access to swap.

Again, this was in low-ram situations.  But, nowadays, with the availability of 1,2,3 or 4 GB RAM .... it really does not matter where you put SWAP.  As in my analogy above ...think of swap as an extra storage that supports RAM.  With so much RAM you have, even if you suspend a lot.

This is what I understood about SWAP.  Someone pls. correct me if I a wrong.

---

### Post by raymondh on 2009-06-14
I also put my swap at the end because it really does not matter with 4 GB RAM.  Also because if one day I decide I no longer need that swap partition, it is simpler (for me) to resize/grow to the right than to extend to the left :)

Good luck.

---

### Post by merlinus on 2009-06-15
+10

Been there, done that.  swap at the end makes it much easier to change things around.  Moving and/or resizing partitions is a lengthy process, so why make it more difficult.

And fwiw, I have never seen my swap partition used, not even when I only had 1.5G ram.

---

### Post by nmaster on 2009-06-15
and raymond, do you have any opinions/suggestions about my logical vs. primary parition question?

---

### Post by raymondh on 2009-06-15
> **neal.m.master said:**
> and raymond, do you have any opinions/suggestions about my logical vs. primary parition question?

I like extended and logicals for the simple reason that using such (extended) will allow me the flexibility of various, numerous logical partitions inside with the only limitations being the OS's capability to number them as well as the actual amount of HD space available.  Remember that you have a 4 partition limit (whether primary or logical).  With a typical windows install (coming from an OEM) .... and windows preferring to deal with primaries ..... you already have at least 2 primaries (recovery and C: drive).  Some OEM's even have a 3rd primary in there (my dell which came with a dock is one type).  That means, for us adventurous souls, that we only have from 1-2 remaining partitions left.  Sure, we can squueze an ubuntu in there but what if ..... you decide to have a separate /home, a separate /data, a separate /var, a separate /user aside from root (/) and SWAP?  You get my point why I prefer Extended and logicals.

Windows and it's documentations will say that we are allowed 3 primary and 1 extended.  To me, that means that windows will deal with an extended the same way it deals with primaries.  Have I followed the 3+1 rule .... nope because I can/have enjoyed the benefits of the extended with.  Just an example ... on my 3 boot netbook (XP + OSX + 8.10), on Ubuntu, I have Ubuntu in an extended partition with root (/), a separate /home as well as swap and a (recent included) /data.  That is a total of 6 partitions all because of the advantages of Extended.

What is the disdvantage of an Extended?  Aside from the fact that it *may* confuse someone who was not involved the actual organization stage ..... and may require additional editing like mount points, etc ... I still have not suffered any lack of visible performance that may make me miserable and question why I did it :)

This may be an long answer but you did ask for my opinion :) ..... I just prefer my ubuntu to be inside a extended.  If you do not plan to grow your system .... there is no harm in using primaries.

Since we are discussing partitions and HD's, let me share with you some links which you may find interesting re: the make up of a actual disk and its' performance hits ... which I think is what we all require from our system ... the best performance possible (or as my son wants ..." one click and it's there, no more waiting, Dad")


This link is about Zone Bit recording.  Note the performance hits on the graphs.

[http://www.pcguide.com/ref/hdd/geom/tracksZBR-c.html](http://www.pcguide.com/ref/hdd/geom/tracksZBR-c.html)

These next 2 involve the make-up of disks

[http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html#toc3](http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html#toc3)
[http://www.ranish.com/part/primer.htm](http://www.ranish.com/part/primer.htm)


Happy Ubuntu-ing.

---


---
title: "Best partitioning scheme?"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by faulkner132 on 2006-01-29
I have an 80 Gig drive with Ubuntu as the only OS.  What is the best partitioning scheme for a new install?

80 Gig for /
or
20 Gig for / and the remaining 60 for /home
or
?

Any suggestions welcome.

---

### Post by Kenotic on 2006-01-29
A seperate /home partition is a very good idea. I have been doing it that way for years.

---

### Post by drummer on 2006-01-29
I have a separate /home partition, very good idea if ever something gets borked or you'd like to do a clean install of a new release. Then you don't have to re do all your user settings, etc. 20gig might be a lot for /, depends on what extra you plan to install other than the base system. I have 10gig for /, 1.5 for swap (probably only need 1 tho) and the rest of my 80gig for /home.

---

### Post by towsonu2003 on 2006-01-29
this would work for me: 

1GB swap (or 512MB?)
10GB / (could go down to 5GB no problem)
rest /home

assuming this is not a server. if it is, you might want to put /var and /tmp to their own partitions as well.

---

### Post by Herman on 2006-01-29
I think start with a swap area at the beginning of the hard drive (outside edge), and one single small ' / ' partition, say about 3.0 or 4.0 GB. Don't add any files to your installation yet. Set it up with all the added software, tweaks and settings you like (automatix etc).
 
 Then use [GParted]("http://gparted.sourceforge.net/livecd.php") on its own live CD to make a duplicate copy the ' / ' partition you tweaked to the end of your drive (center of your hard-disk), as a back-up. Resize your 'working' Ubuntu partition at the beginning of the hard-drive that you are going to use now, to whatever size you need, and start adding and creating files in it and generally using it. 

If you just keep your important files backed up now and anything bad happens to 'bork' your system, you can restore it in a matter of minutes with GParted on its own CD- just copy your back-up partition from the end of your drive to your working partition, put your files in and away you go again! 
You only need a ' / ' partition and a swap area, plus the back-up ' / ' partition. That's my  two cents worth.  :-D (Herman).

---

### Post by faulkner132 on 2006-01-29
Thanks for the replies everyone, this is what I am thinking.

I already have Ubuntu installed on this 80 Gig drive with only a single partition.  This is my first install (up and running for about 3 months now) and now I've got the hang of it, but have hosed a couple of apps due to my own beginner ignorance.  From reading the posts, it appears a clean format is the way to go.  I have a separate drive I'm going to back up my /home partition to, but for the most part, I am just going to rebuild everything.

For partitioning, I think I am going to go with 10 Gig for / and the rest for /home.  I keep all my music and what not on a separate drive, so space will never really be an issue.  I want to make sure I never run out of / space, so it sounds like 10 Gig will be plenty.

Any drawbacks to the method I have chosen?  I just want to make sure I do it right, so when I upgrade to Dapper in about 3-4 months using another clean install that it goes smoothly.

Thanks again for your input.

---

### Post by towsonu2003 on 2006-01-29
[quote=faulkner132]For partitioning, I think I am going to go with 10 Gig for / and the rest for /home.  [/QUOTE]
that looks fine to me, but don't forget the **swap** partition...

---


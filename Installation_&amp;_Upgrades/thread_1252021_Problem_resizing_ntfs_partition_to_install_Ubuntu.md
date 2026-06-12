---
title: "Problem resizing ntfs partition to install Ubuntu"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by j_cook on 2009-08-28
Hello everyone,

I'm not sure if this has been covered (I've searched multiple times, but to no avail), so if this was already covered, could you please point me in the right direction?

I currently own a HP Mini 1151NR netbook. It has a 80 GB hard drive which is taken up by a ntfs Windows XP partition. My goal is to resize this partition to make room for Ubuntu 9.04. I would love to just wipe the whole hard drive and just install linux, that would be a dream, but until I can a) find a way to use my internal EVDO card on Ubuntu b) cancel my 3g netbook plan, I can't delete my windows partition. So, if I want linux I need to resize this ntfs partition to make room for it (other than running Jaunty from a flash drive, which is what I'm doing now...). Here is my problem:

When I run the live CD, and use gparted, it won't let me resize the ntfs partition. There is a caution sign on the partition, so obviously there is some sort of problem. When I right click and go to properties, here is the warning I get:

Warning

ntfsresize v2.0.0 (libntfs 10:0:0)
Device name :/dev/sda1
NTFS volume version: 3.1
Cluster size :4096 bytes
Current volume size: (80016 MB)
Current device size: (80016 MB)
Checking system consistency...
Cluster 1081024 is referenced multiple times!
Cluster 1586362 is referenced multiple times!
Cluster 1586363 is referenced multiple times!
Cluster 1586364 is referenced multiple times!
Cluster 1586365 is referenced multiple times!
(continues off of screen)

Yes, I have defraged my hard drive three times (it took two to get my BRAND NEW hard drive clean...the thing came fragmented...) and no, I don't know what to do.

If this warning is not the issue, then I don't know why it's not letting me resize this file. Everywhere I have read says that you simple resize it. It'll let me resize it up (because there is still a miniscule amount of space left after the partition), but it won't let me resize it down.

I hate running Windows, and running Ubuntu on my flash drive (BOAS - Buntu On A Stick, as I like to refer to it as) is slow. So help would be greatly appreciated.

Thanks!

---

### Post by stlsaint on 2009-08-28
> **j_cook said:**
> Hello everyone,

I'm not sure if this has been covered (I've searched multiple times, but to no avail), so if this was already covered, could you please point me in the right direction?

I currently own a HP Mini 1151NR netbook. It has a 80 GB hard drive which is taken up by a ntfs Windows XP partition. My goal is to resize this partition to make room for Ubuntu 9.04. I would love to just wipe the whole hard drive and just install linux, that would be a dream, but until I can a) find a way to use my internal EVDO card on Ubuntu b) cancel my 3g netbook plan, I can't delete my windows partition. So, if I want linux I need to resize this ntfs partition to make room for it (other than running Jaunty from a flash drive, which is what I'm doing now...). Here is my problem:

When I run the live CD, and use gparted, it won't let me resize the ntfs partition. There is a caution sign on the partition, so obviously there is some sort of problem. When I right click and go to properties, here is the warning I get:

Warning

ntfsresize v2.0.0 (libntfs 10:0:0)
Device name :/dev/sda1
NTFS volume version: 3.1
Cluster size :4096 bytes
Current volume size: (80016 MB)
Current device size: (80016 MB)
Checking system consistency...
Cluster 1081024 is referenced multiple times!
Cluster 1586362 is referenced multiple times!
Cluster 1586363 is referenced multiple times!
Cluster 1586364 is referenced multiple times!
Cluster 1586365 is referenced multiple times!
(continues off of screen)

Yes, I have defraged my hard drive three times (it took two to get my BRAND NEW hard drive clean...the thing came fragmented...) and no, I don't know what to do.

If this warning is not the issue, then I don't know why it's not letting me resize this file. Everywhere I have read says that you simple resize it. It'll let me resize it up (because there is still a miniscule amount of space left after the partition), but it won't let me resize it down.

I hate running Windows, and running Ubuntu on my flash drive (BOAS - Buntu On A Stick, as I like to refer to it as) is slow. So help would be greatly appreciated.

Thanks!


are you running windows now and if you are than you should use the disk management tool to partition the ntfs hdd...thats if your on vista!!

---

### Post by j_cook on 2009-08-28
When I open up Disk Management in XP it gives me everything I would want to know about it but doesn't give me any option to resize the partition.

---

### Post by stlsaint on 2009-08-28
ok so your in xp...now i dont see why you would have to do this but have you tried right clicking on the hdd in partition editor(gparted) and checking out the options on the hdd. If it says anything about mounting or anything like that than you need to unmount then resize...also you can try something like acronis disk suite or actvie disk suite...they are great for partitioning drives. and with the cluster errors it looks like you may have a faulted hdd!!

---

### Post by j_cook on 2009-08-28
Yep, checked that. When I booted into Ubuntu the first time to partition it, I checked if it was mounted, and it wasn't. Are those apps for windows or linux?

If it's faulted then that explains why it was fragmented to begin with...

---

### Post by stlsaint on 2009-08-28
those apps are not os specific...they boot to themselves and you can adjust hardware, files etc...i will have to double check for within linux tho but since you dont have linux installed yet they will easily see ntfs and all other formats outside of ext 2/3/4...try one of them and see...or try a different hdd!

---

### Post by presence1960 on 2009-08-28
> **j_cook said:**
> 
If it's faulted then that explains why it was fragmented to begin with...

Actually some of the worst fragmentation I have ever seen is after a new install. So that is normal.

---

### Post by raymondh on 2009-08-28
AFAIK ... XP's disk manager does not give the option to resize down.  Only enlarge.

Why not use the automated install (ubiquity) to allocate the partition? Defrag multiple times.  Presence is right about fragemented drive/s after an initial install.  Then, boot into your ubuntu install medium and when you get to step 4, select side-by-side.  You will be given the option to grab a slider (using your mouse or trackpad) and slide to allocate sizes for both XP and Ubuntu.

I suggest this as an alternative to using gparted (or another 3rd party editor) and, if you have no intentions to create separate /home settings, etc.

Good luck.  Back-up.

EDIT : this is what the [slider]("http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874") looks like ..... thanks to presence ;)

---

### Post by j_cook on 2009-08-28
Windows lies to me. That's all I have to say.

I defraged it three times yesterday. THREE TIMES! And it said (and showed) that the thing didn't need defraged again. Then I have troubles with partitioning because of the cluster errors. 

Today, I look and the thing is filled with fragments again! After a defrag the FOURTH time, it finally let me resize my hard drive. Moral of the story: Keep spamming defrag on windows even after it tells you to stop...

*rant over*

Thank you for all your help! Everyone was a great help! I'll just be happy when I don't have to use it anymore...

---

### Post by raymondh on 2009-08-28
congratulations ... happy ubuntu-ing

---

### Post by stlsaint on 2009-08-28
> **raymondhenson said:**
> AFAIK ... XP's disk manager does not give the option to resize down.  Only enlarge.

Why not use the automated install (ubiquity) to allocate the partition? Defrag multiple times.  Presence is right about fragemented drive/s after an initial install.  Then, boot into your ubuntu install medium and when you get to step 4, select side-by-side.  You will be given the option to grab a slider (using your mouse or trackpad) and slide to allocate sizes for both XP and Ubuntu.

I suggest this as an alternative to using gparted (or another 3rd party editor) and, if you have no intentions to create separate /home settings, etc.

Good luck.  Back-up.

EDIT : this is what the [slider]("http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874") looks like ..... thanks to presence ;)


thanks just learned something from you and ubuntu never ceases to amaze me day in and day out!!

---

### Post by raymondh on 2009-08-28
> **stlsaint said:**
> thanks just learned something from you and ubuntu never ceases to amaze me day in and day out!!

I should've said ... the default disk manager in XP.  Users can download and install diskpart.exe but, that tool is command-line based (not GUI).

It (as well) amazes me and keeps me curiously motivated to learn.  I am not GURU .... I just know enough to realize I need to learn more :)

Happy Ubuntu-ing.

---


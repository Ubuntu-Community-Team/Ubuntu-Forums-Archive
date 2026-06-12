---
title: "Why is it not installing after many hours"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by bob1776 on 2009-04-18
Hello,

I am new to this forum and have only played a little with ubuntu.  I was attemping to install 9.04 to my system from the live CD and am seeing the following problems which I do not understand.

Background.  System is a E6600 4GB 320GB SATA dual boot XP/2003

I wanted to add 9.04 onto this system and before the install, I did serveral passes of defrag.  

The 320GB disk was one partition so I planned on using that for my install.

When I ran the install I had the following problems:

1.  Between Steps 3 and 4, the install seem to sit there for at least 2 hours. There was no clue that it was doing any thing or even what it was doing.  I think that it was checking partitions but my question here is why it would take 2+ hours to do this.

2.  When it finally responded, in step 4, I chose to use the slider to designate 60GB for the ubuntu partition.  It opened a popup box that said it was resizing the partition.  The next morning, it looked exactly the same...the progress bar still showed 0% done.

3.  I canceled the install at this point and when windows rebooted, it ran checkd so I assumed that the install had mucked with the disk and partitions.  After reboot, I noted that a 60GB partition was created.

4.  I attempted to reinstall at this point, and again between step 3 and 4, it was not completing this action so after about 15 minutes, I canceled and started ubuntu in live CD mode.  

5. I then started GPartd and attempted to scan the partitions.  After about 1 hour, I tried to cancel this action but it ignored me.  Finally canceled the process and rebooted windows.

From this, I have a couple of issues

1.  Why does it take so long to partition the disk.  This does not give me confidence in the software.

2.  Why is there no clue or progress bar between steps 3 and 4 to let the user know what it is attempting to do?


Thank you for listening...
Bob

---

### Post by Ericyzfr1 on 2009-04-18
Did you try to format smaller partitions? If you want to use large partitions, have you tried to format them with Gparted Live CD?
I use 10GB for / and 5GB for /home and it takes a couple of minutes. Anything larger, I use Gparted.

---

### Post by bob1776 on 2009-04-18
In item 5 of my post, I tried GPartd just for that reason although I did not think that 50GB was that large of a partition.  It started a scan of the partitions and never came back.  How long should it take to scan 5 partitions to get the info about them.  Is it trying to read every file in every partition? 



Bob

---

### Post by hesjnet on 2009-04-18
I have used the Ubuntu installer to make 100-200 GB partitions several times. It never takes many hours. Maybe you burned the iso with maximum speed on a cheap disc without testing the integrity after burning?  Try to burn another disc at a lower speed, wich often can make a big difference, and try again.

Ps. If you don't already do so, it is also possible to use an USB thumbdrive to install ubuntu. Try [Unetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by kelsey.chris on 2009-04-18
Does your XP install have any Norton products on it?  I had an issue with Norton Ghost messing up my partitioning.  Apparently it sets up a 'ghost' partition in the master boot record.  Apparently new systems with recovery partitions have something similar.  
I ran the Norton removal tool [http://service1.symantec.com/Support/tsgeninfo.nsf/docid/2005033108162039]("http://service1.symantec.com/Support/tsgeninfo.nsf/docid/2005033108162039")  To free myself of that mess.
Hope this helps.  I still keep an XP partition for playing steam games, but for everything else, Ubuntu is just easier.
Chris

---

### Post by bob1776 on 2009-04-18
I had verified the CD before, but did it again to be sure and it passes with no problems reported.

I went in with windows and formated that 60GB partition that it created on the first install attempt as a standard ntfs partition in case it had gotten trashed in the aborted install.  This did not help,  it is now 25 minutes into the transition from install step 3 to step 4 and I am assuming it is reading the partitions but don't have a clue why it takes so long.

As far as Norton Ghost, no it has never been installed here.  One of the reasons I am looking to get ubuntu going is to replace this xp install since it is xp64 and is not very well supported.  I installed it because of the 4 GB of memory but half the applications in the world barf at it. I haven't even put Partition Magic on this system.

---


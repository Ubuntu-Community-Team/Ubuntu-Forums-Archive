---
title: "Why no sticky re general IDE bug?"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by bsmith1051 on 2007-07-09
I've got a relatively new clean-install of 7.04 and I started to suspect something was wrong because the system was soooo slow whenever I was using the hard drive.  Then I started to find LOTS of forum discussion and blogs talking about a bug in the Linux kernel that is causing problems for just about everybody.  Now it's on Slashdot.  But I've yet to see any general announcement, e.g. a sticky note, here on Ubuntuforums.

Is Ubuntu.org aware of this problem?  Do they have any suggestions for coping with it, or any idea when it will be fixed?

One post I saw referred to disabling dual-core by setting append="nosmp" in lilo, but I don't know how to do this.  I've never touched my lilo setup!  Another post said it was only an issue when you had a CD or DVD drive with no disc inserted.  Others have said it's limited to Nvidia chipsets while still others have said it's a general kernel bug affecting all chipsets.

Another point of confusion for me is that my system appears to be running 'sata-nv' (and No I don't remember what command I saw to check this...) whereas I'd previously seen a HOW-TO for Linux/SATA which seemed to indicate that my newer Nvidia 6100 chipset was supported under the general 'libata' driver.  Or am I confusing still more things here?

Any help would be greatly appreciated!

---

### Post by fredj on 2007-07-09
The only problem I have noticed was that my system would freeze for several seconds every hour or so.
I fixed this by upgrading the firmware in my DVD drive.

---

### Post by charles_elwood on 2007-07-09
Can you be more specific as to the articles. I'm trying to track down an issue that's causing <3MB/s throughput on my PATA drives since I /upgraded/ to feisty.

---

### Post by bsmith1051 on 2007-07-10
Other Ubuntuforum posts,
[http://ubuntuforums.org/showthread.php?t=471255](http://ubuntuforums.org/showthread.php?t=471255)
[http://ubuntuforums.org/showthread.php?t=447474](http://ubuntuforums.org/showthread.php?t=447474)
[http://ubuntuforums.org/showthread.php?t=449001](http://ubuntuforums.org/showthread.php?t=449001)

Ubuntu bugs,
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/31766](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/31766)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114236](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/114236)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730)

Linux Kernel bug,
[http://bugzilla.kernel.org/show_bug.cgi?id=7372](http://bugzilla.kernel.org/show_bug.cgi?id=7372)

Slashdot discussion,
[http://linux.slashdot.org/comments.pl?sid=247219&cid=19797955](http://linux.slashdot.org/comments.pl?sid=247219&cid=19797955)

Gentoo discussion,
[http://forums.gentoo.org/viewtopic-t-482731-start-450.html](http://forums.gentoo.org/viewtopic-t-482731-start-450.html)

---

### Post by charles_elwood on 2007-07-11
Thanks. I think that hits the nail on the head. I have a workaround by using the old ATA drivers.

---

### Post by frodon on 2007-07-11
bsmith1051, in your post you are mixing completely different bug reports, some are related to kernel 2.6.15, some other to kernel 2.6.20, some report freeze, some other report slowdowns, some concern SATA drivers, some other IDE drives.

Could you be more accurate and tell us which bug you are talking about ?

Anyway rather than requesting a sticky (which won't solve the problem) i strongly advice you to fill a bug report thus things are more likely to move faster.

---

### Post by bsmith1051 on 2007-07-11
> **frodon said:**
> you are mixing completely different bug reports, some are related to kernel 2.6.15, some other to kernel 2.6.20, some report freeze, some other report slowdowns, some concern SATA drivers, some other IDE drives.  Could you be more accurate and tell us which bug you are talking about ?
This is my point exactly -- no one seems to know what's really going on.  It's primarily being reported as a problem with SATA drives and on kernels after 2.6.17.  Sometimes people think it's 'solvable' by disabling their 2nd CPUs, other times by leaving a disc in their IDE optical drive.  All I personally have to contribute (which is not sufficient to file a bug) is that my brand-new Ubuntu 7.04 acts like it's running on PIO-mode hard drives despite have an Athlon X2 5600, dual SATA2 drives in RAID1 mirror, and 2 GB of RAM.  My hard-drive performance should rock! . . .

---

### Post by frodon on 2007-07-12
Have you tried playing with sdparm ?

Anyway without detailed infos about your hardrive configuration no one will be able to help you.

---

### Post by bsmith1051 on 2007-07-12
> **frodon said:**
> Have you tried playing with sdparm ?
I don't know what that is.  I'm not looking for individual attention at this point, else I would post more detail.  Instead, as I've tried to demonstrate, there appears to be a very common bug with SATA and all recent kernels.  So I was hoping that someone more knowledgeable than I could offer guidance, e.g. "do this test procedure to see if you're having the problem, then try these possible workarounds to see if any of them relieve the problem."  And, again, I think this (the How To instructions, not this current now-rambling post) should be a sticky.

---

### Post by frodon on 2007-07-12
> **bsmith1051 said:**
> And, again, I think this (the How To instructions, not this current now-rambling post) should be a sticky.Without clear explanations of what the bug is and what it affects it wouldn't have sense.

About sdparm i am not more knowledgable than you but i know it is the tool to configure sata drives so maybe you should try to get some knowledge about it and see if there's something useful with this tool for your problem. I don't have sata drives, just IDE so i can't test it.

---

### Post by bsmith1051 on 2007-07-12
another long discussion,
[http://ubuntuforums.org/showthread.php?t=400356](http://ubuntuforums.org/showthread.php?t=400356)
They claim there's a big problem between Edgy and Feisty.

Again, I don't understand why there isn't a general note from Ubuntu org about these problems.

---

### Post by frodon on 2007-07-13
> **bsmith1051 said:**
> Again, I don't understand why there isn't a general note from Ubuntu org about these problems.For the reason stated in my previous post.
This bug about hdparm not being able to set dma because IDE drives are handle by sata drivers now is already reported and don't affect everybody because the default config already enable dma, the slowdown issues don't seem directly related to this even if those who have this bug have slow drives.

Anyway like i said before bug reports are more useful than stickies on this,to repeat myself without clear explanations of what the bug is, clear details on what it affects and what are the workaround a sticky has no sense for me.
Anyway if you still think despite my post that it deserves a sticky then you can post a request in the "forum feedback" forum where you will get opinions from other staff members.

---

### Post by KubuntuKilledMe on 2007-07-13
Sticky it. Not sticking it its stinky politics. Ubuntu is B R O K E N right now for many ppl. Deal with it.

---

### Post by PriceChild on 2007-07-13
btw I don't think this was a bug... rather a feature that everything is handled by libata.

---

### Post by KubuntuKilledMe on 2007-07-13
Not a bug but a feature? I must be lost, i didn't mean to post in the microsoft forum.

---

### Post by dabl on 2007-07-13
Here's my hdparm output, running Kubuntu 7.04 32-bit.  First drive is a 200GB Maxtor IDE/PATA, the second two are WD1500 SATA drives.  Should I be concerned about these numbers?

```
dabl@feisty:~$ sudo hdparm -tT /dev/sd?
Password:

/dev/sda:
 Timing cached reads:   8570 MB in  2.00 seconds = 4288.42 MB/sec
 Timing buffered disk reads:  186 MB in  3.03 seconds =  61.40 MB/sec

/dev/sdb:
 Timing cached reads:   8740 MB in  2.00 seconds = 4373.67 MB/sec
 Timing buffered disk reads:  254 MB in  3.02 seconds =  84.16 MB/sec

/dev/sdc:
 Timing cached reads:   8720 MB in  2.00 seconds = 4363.04 MB/sec
 Timing buffered disk reads:  248 MB in  3.02 seconds =  82.16 MB/sec
```

Thanks.

---

### Post by bsmith1051 on 2007-07-13
> **dabl said:**
> Here's my hdparm output, running Kubuntu 7.04 32-bit.  First drive is a 200GB Maxtor IDE/PATA, the second two are WD1500 SATA drives.  Should I be concerned about these numbers?
They seem kick-*** to me!
______________________________________

Here's some more justification for there being a sticky:

1. still more related posts,
[https://bugs.launchpad.net/ubuntu/+bug/90531](https://bugs.launchpad.net/ubuntu/+bug/90531)
[http://lkml.org/lkml/2007/1/6/119](http://lkml.org/lkml/2007/1/6/119)

2. I tried testing my old machine (AMD-2100, 768 MB, Seagate 160 SATA) with the following three LiveCDs and running hdparm -Tt

Edgy (kernel 2.6.17-10) = 795 KB/s, 55 KB/s
Feisty (kernel 2.6.20-15) = 401 KB/s, 56 KB/s
Gusty (kernel 2.6.22-7) = 392 KB/s, 56 KB/s

So, it seems clear that performance when accessing the disk cache ("timing cached reads") has plummeted since Edgy.  That 2nd post (from kernel mailing list) says there's an issue with the [cfq] scheduler and that switching to the 'anticipatory' scheduler fixes it.  But I was unable to figure-out how to test that.

And I still haven't tried these tests on my new machine.

---

### Post by bsmith1051 on 2007-07-13
How's this for a possible sticky note:

**Troubleshooting hard-drive performance**

This assumes that you have a bootable install of Ubuntu but you think it's not running correctly.  Many people have reported that the upgrade from Edgy (6.10) to Feisty (7.04) has made their computers much slower.

1. Do a quick speed test
(you need to know the device name of the hard-drive, e.g. /dev/hda)
```
sudo hdparm -Tt /dev/hda
```
The first number (timing cached reads) measures how fast the software configuration is working.  A typical value is 1000 KB/s but anywhere from 400-4000 is possible (and normal for a particular machine)

The second number (buffered disk reads) measures how fast the physical drive is working.  A typical value is 50 KB/s.

2. Boot the Edgy 6.10 LiveCD and re-run the speed test.  If your cached-reads is dramatically faster, join the club!

3. Identify which kernel you're using 
```
uname -a
```
4. Identify your controller and drives
```
lspci | grep ATA
dmesg | grep ATA
```
or for painful details
```
lspci -vvnn
```
5. check your hard drive's configuration (the same command but in 3 stages of successive detail)
```
sudo hdparm /dev/hda
sudo hdparm -i /dev/hda
sudo hdparm -I /dev/hda
```
Check that "using_dma" is ON.  Also, IO_Support should probably be '32-bit' though this depends on how old your computer is.  For more information about these commands and settings, try this link [http://linuxgazette.net/issue79/punk.html](http://linuxgazette.net/issue79/punk.html)

6. review your startup messages
```
dmesg
```
to save this printout to a file 'dmesg.log'
```
dmesg > dmesg.log
```
It's painful to try and read but look for any mention of 'timeout' or other errors.

---

### Post by bsmith1051 on 2007-07-25
Sounds like the problems I've described are explained by this article,
[http://apcmag.com/6735/interview_con_kolivas](http://apcmag.com/6735/interview_con_kolivas)

Basically, there are known kernel problems with desktop interactivity during hard drive I/O but it's not a concern for developers.

---

### Post by vexorian on 2007-07-25
hmm bsmith1051, you are mixing way too much things into the same issue, and the Kolivas interview kind of hit the limit...

Not really wanting to discourage you but make sure to divide each bug, they are different things.

This is actually the first time I read about this IDE bug, so it may not be soo important, if we had stickies for each bug, the stickies would use all the forum page and it would make the navigation harder.

So far though I heard of 2 ways to make it freeze, one is this  IDE thing and the other one is caused by an specific wifi driver.

---

### Post by bsmith1051 on 2007-07-26
I appreciate that you think I'm an inexperienced user, wildly reporting every glitch.  And believe me, I'm frustrated that I don't have a better way to quantify the problem.  But as the link/interview points out -- and by one of the better-known kernel developers -- there's a general decline in the performance of 'desktop' computing under Linux and it's hard to define.  I started this whole thread because I knew there was *something* wrong with my hard drive performance but didn't know how to prove it.  So I asked for input and received a lot of sincere (but misguided?) requests to try and fix my system.  But without knowing what specifically is wrong that's pretty hard, right?  Sure, I could post all the configuration files for my system plus the hdparm results but I don't think there's anything wrong with the setup of my computer, I think there's something wrong with the installed software.  So instead I've tried to focus on the potential Larger Issue here -- which various replies have tried to discount.  I posted links to lots of possible-related posts and was criticized for not somehow posting a link to The Answer.  Now I think I might have managed to do so, i.e., the link to the interview where someone far more knowledgeable than I is saying the same thing I'm saying (only more accurately) and again I'm being criticized.  Perhaps I should start a new thread, e.g. "Why no sticky re general performance problems with Linux" ?  According to the interview, that might be more accurate.

P.S.  What did you think of my proposed Troubleshooting note?  Did it hit the limit, too?

---

### Post by frodon on 2007-07-26
BTW, if you are such frustrated, why don't you make a backup of your ubuntu partition just in case and upgrade to gutsy gibbon ?
Because it's been said that this issue won't be fixed in feisty but will be in gutsy so if i was you i would give gutsy gibbon a try,burn the tribe 3 CD, boot it and see what are you disk performances, if they are good then concider upgrading to gutsy now.

---

### Post by vexorian on 2007-07-26
> **bsmith1051 said:**
> I appreciate that you think I'm an inexperienced user, wildly reporting every glitch.  And believe me, I'm frustrated that I don't have a better way to quantify the problem.  But as the link/interview points out -- and by one of the better-known kernel developers -- there's a general decline in the performance of 'desktop' computing under Linux and it's hard to define.  I started this whole thread because I knew there was *something* wrong with my hard drive performance but didn't know how to prove it.  So I asked for input and received a lot of sincere (but misguided?) requests to try and fix my system.  But without knowing what specifically is wrong that's pretty hard, right?  Sure, I could post all the configuration files for my system plus the hdparm results but I don't think there's anything wrong with the setup of my computer, I think there's something wrong with the installed software.  So instead I've tried to focus on the potential Larger Issue here -- which various replies have tried to discount.  I posted links to lots of possible-related posts and was criticized for not somehow posting a link to The Answer.  Now I think I might have managed to do so, i.e., the link to the interview where someone far more knowledgeable than I is saying the same thing I'm saying (only more accurately) and again I'm being criticized.  Perhaps I should start a new thread, e.g. "Why no sticky re general performance problems with Linux" ?  According to the interview, that might be more accurate.

P.S.  What did you think of my proposed Troubleshooting note?  Did it hit the limit, too?
I appreciate that you are on the defensive for no reason, but the interview was totally unrelated to your problem and most of the links you posted were. The problems the interview talks about are related to the kernel itself and not sata drivers....

Regarding your fix guide you probably could post it in the howto section, again an sticky is not necessary.

I know this bug is pretty important to you, but that doesn't mean it should be stickied, it is simply problems with your specific hardware , if everyone else's problems with specific hardware got sticked, this would not be ubuntuforums.org but launchpad.net , and we already got a launchpad.net ...

---

### Post by bsmith1051 on 2007-07-26
> **vexorian said:**
> I appreciate that you are on the defensive for no reason, but the interview was totally unrelated to your problem and most of the links you posted were. The problems the interview talks about are related to the kernel itself and not sata drivers....
huh? Go to the 2nd page of the interview and search for "large file"
[http://apcmag.com/6759/interview_with_con_kolivas_part_1_computing_is_boring](http://apcmag.com/6759/interview_with_con_kolivas_part_1_computing_is_boring)
That sounds exactly like what I've been experiencing.

re Gutsy beta, I've got a copy of it but didn't think it solved my problem.  I can't remember off-hand if I already tried the hdparm test or if I read other people who said they'd tried it.  I'll try to find my notes..  And, the dramatic drop in hdparm 'cached reads' performance may or may not be significant.  It's at least consistent!!...

EDIT:  Doh!  Look at my previous post #17.  I tried Gutsy but it was even slower on cached reads than Feisty!

---

### Post by vexorian on 2007-07-26
I am sure such an ambiguous (and probably exaggerated) claim by Con Kolivas is refering exactly to your precise issue. Either way I did not experience any of the problems he claims and my hardware is 4 years old...

---

### Post by bsmith1051 on 2007-07-26
so because you personally are not experiencing a problem means that it can't be a bug?  All that means is that it's not a ubiquitous bug.  My equipment is 2 months old and behaves exactly as he described.

---

### Post by frodon on 2007-07-27
> **bsmith1051 said:**
> re Gutsy beta, I've got a copy of it but didn't think it solved my problem.  I can't remember off-hand if I already tried the hdparm test or if I read other people who said they'd tried it.  I'll try to find my notes..  And, the dramatic drop in hdparm 'cached reads' performance may or may not be significant.  It's at least consistent!!...

EDIT:  Doh!  Look at my previous post #17.  I tried Gutsy but it was even slower on cached reads than Feisty!Please forget cached reads and hdparm, just test you drives performances copying big files from one drive to another.

You tested the tribe 3 CD or the previous version ?

---

### Post by bsmith1051 on 2007-07-27
> **frodon said:**
> You tested the tribe 3 CD or the previous version ?
Tribe 2, which was current at the time.

How do I write a batch file to exactly time a file copy?  I know how to do it in DOS/Windows but not in *nix.
________________

EDIT: nevermind, I found the 'time' command.  sweet.  here's my test:

> (20) 350MB .avi files from 2nd HD to "1st" (actually the RAID-1 combo) = 6.8 GB @ 3:24.5s = 33.3 MB/s

I experienced sporadic lock-ups in the desktop but never for more than about 1-2 sec.   I wonder if it would have been worse if it'd been 1 single giganto file?
___________________

EDIT #2: I just did a test with an 11.1 GB file, going from the RAID-1 to the 2nd HD.

> 11.1 GB @ 5:03.9 = 36. 5 MB/s

The desktop only froze-up once during the copy and then only for a moment.  So that makes me feel a lot better.  Maybe the problems I was experiencing were from copying on the same drive.  Now that I've got my 2nd drive online I shouldn't have to do that anymore.

---

### Post by bsmith1051 on 2007-08-09
Just to beat this horse a bit more, it turns out I'm _really_ not the only one noticing a problem with IDE performance.  And it sounds like people in the know have known the problem (and a workaround) for a long time,
[http://kerneltrap.org/node/14148](http://kerneltrap.org/node/14148)

So, can anyone tell me if Ubuntu defaults to "atime" or "noatime" ?  The current kernel default is "atime" which all the kernel developers -- including some guy named Linus(?) -- all agree is unnecessary except in one old situation.  But one poster said that they think Ubuntu defaults to "noatime"...

FYI - apparently this disables the Last Access Time feature?  Obviously, it's nice to have this info but if it kills the performance of a journaling file-system (like ext2/ext3) I would rather go without it.

---


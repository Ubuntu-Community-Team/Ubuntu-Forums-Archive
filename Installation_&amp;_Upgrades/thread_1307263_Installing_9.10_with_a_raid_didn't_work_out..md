---
title: "Installing 9.10 with a raid didn't work out."
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by bamboomy on 2009-10-31
Like I kinda suspected and kinda worded in this thread:

[http://ubuntuforums.org/showthread.php?t=1293294](http://ubuntuforums.org/showthread.php?t=1293294)

(not for sensitive people because of 
-> 'trolling'
-> 'being a book'
-> ... (if you're still interested, read the whole thread)
)

Anyway,

I'll try not to repeat myself, but I feel this is going to be another 'book', I will try not to troll, but the post might be provocative. 

Above all this thread is intended to get help but I might be quite negative from time to time.

Sorry beforehand.

Ok, after this introduction, pep-talk, trying to be positive, hup hup, go bamboomy.

1)The present situation:
- I have now a 9.10 installation, but alas it, thus far, didn't managed to be booted. The exact layout I will explain in a minute.
- I have a windows 7 that (believe it or not) I'd like to see booted
- I have a RAID1 installed, I installed it from the BIOS (I think it is a hardware RAID but I'm not sure, yet again, the situation will be more in detail later) The RAID is partitioned in two partitions, and formatted, from windows 7 in ntfs and, because ntfs support is just great these days I'd like to leave it that way because I'd like to be able to access those partitions from windows.
--> The RAID is also set up from the (last) alternate 9.10 install I tried, but, like I said, I don't know whether 9.10 sees it...

That is the software part of the current setup.

The hardware part:

The RAID exists out of 2 identical disks who work fine under windows and are recognized as the two partitions they should be.
I have 1 other (mother) disk where I put the OS's on, initially this was a faster disk because I was under the impression that that would increase the windows system index but it didn't. I managed to get windows 7 and 9.10 installed on that initial disks but at boot time 9.10 alerted me that there were much bad sectors. I bought a (smaller, slower and cheaper) disk where I did the following on:

A)Install windows 7
(without mentionable trouble)

B)Install ubuntu 9.10 alternate

And that is where the trouble started...

In the numerous attempts I did I remember following situations:
i)errors whilst installing
ii)reboot, install went great, reboot ended up in windows (no grub)
iii)reboot, install went great, reboot, nothing (system didn't recognized grub)

C)At this point I found myself in a familiar situation with the false believe that a similar approach would result in the desired setup. 

Oh, how I was wrong.

I thought: no problem, I just use my 9.04 cd, install that, upgrade to 9.10 and everyone (especially me, but also all of the people of mentioned thread) will be happy.

To my great surprise however, after finishing the installation (of 9.04) grub (0.97) _didn't_ come up. It "didn't load", "didn't start" (some searchterms I googled on), it didn't do anything.

(I believe 'no boot disk found, insert bootable medium and press key' is the error my BIOS (repeatedly) displayed.)

Disappointment, yet again.

D)First attempts without grub2

My first approach was reinstalling the alternate, but with higher interaction so I could decide whether I'd wanted to install grub2, grub or (heaven forbid) lilo (that was something I didn't try, could lilo have saved me?).

-=caution, high troll level in following paragraph, if not wanting to be provoked, skip reading until -=end troll=- token==--

-> I was kinda surprised, reading the dialog with which the question whether I wanted to use grub0.97 or grub2...
-> The kind people of the mentioned thread informed me that I shouldn't whine about not working beta software, yet the dialog informed me of the fact that grub2 _was_ experimental/beta software and that it might cause trouble and that it shouldn't be used on production environments.
-> However, the standard installation, in my perception, uses grub2 by default, without even giving the option. It seemed that a very important point in my 'not very informative rant book thread' seemed to be right on the spot, but, hey, with a 72.31% of people who disagreed with me and only 7.69% agreeing, and with the democratic principle that the majority is right, I am now running a system with both Windows 7, Ubuntu 9.10 and a fully operational RAID1, but I might be someone with a slight problem of perceiving the reality the right way probably...

-=end troll=-

E)Trying to hack grub onto the disk

After that I booted (several times) the 9.04 install cd, searching the world wide web, looking for salvation.

There was one blog that looked very promising, it spoke of chrooting into your installed system and run grub from that environment, alas, no vail.

Grub doesn't seem to complain about anything. It 'successfully' installs itself onto the mbr, (hd0), it finds my installation on (hd0,1), everything seems to be a-ok but for some reason it never manages to make the jump from the BIOS unto, well, itself.

Could it be that, forgive me the term, evil grub2 messed up my mbr so much that it's ancestor grub0.97 can't repair the damage?

Should I reinstall windows and return to the dark side after years in the light?

Should I try another distro? Am I not human enough for ubuntu? (the RAID is maybe to Borg-like, I feel the nano-probes starting to develop, will I turn into the father of all Borg and take over this planet?)

Maybe there is salvation in the answer to this question:

What would Jesus do?

(excuse my literal freedom, I'm drinking a cold whiskey-coke at 4:35 in the morning, but hey, I will rule the planet, what do I care? ;))

Anyways:

2)Temporary solution.
As one last shot I will try to do the chroot thingy with my alternate cd.

Then I will try whether windows is able to be made bootable again so I at least have one OS that wants to boot.

If those two options fail, then I'm going to put the bad-sector drive back in, tomorrow, while the disk is slowly degrading I hope some reactions will follow on this thread. After posting it I will crawl into my nice, warm bed and dream about world domination.

3)Your input.

If you have made it this far in my 'book' I'd like to know whether you have a solution for my problem.

I don't have high hopes.

I _did_ google and found that people encountered similar problems, but apart from the blog I mentioned, (although the writer insisted on bookmarking his post I didn't and I can't find the reference anymore. Maybe you can but it doesn't matter because that didn't help.) I didn't find much hopegiving reactions.

Ok, time to sleep now,

thanks for your reactions and thanks for reading,

S.

ps:one final edit before I hit the sack: 9.10 looked quite promising, that is also the reason why I tried it. It 'passed my test'. It's only a shame that it doesn't boot, and that it also prevents me from booting another os...

Many thanks to the people who made 9.10 such a great release, audacious2 doesn't scramble my songs any more (but that could have also been caused by the bad sectors) but being it bootable would be nice though...

---

### Post by jsynesio on 2009-10-31
Put /boot on a separate partition. I had this problem on 9.04 when I tried to install Raid6 with an Intel SRCSATAWB controller. I did a fresh install of 9.04 with /boot on a separate 200Mb partition and my machine booted fine. 

I have just done a fresh install of 9.10 amd64, but this time I let Ubuntu do the partitioning. I see a 1Mb bios_grub partition (sda1), and ext4 partition (sda2) and a linux-swap partition (sda3). Ubuntu boots fine. 

I hope this helps.

---

### Post by bamboomy on 2009-10-31
I just reinstalled windows 7,

it booted,

confidently about 9.04 being able to boot properly I downloaded the alternate from that version.

After installing that the following now is the case on my computer:

-> It boots (yey)
... in the dual boot screen of _windows_!!!

I now have the option to choose between a (deleted) windows 7 and a (reinstalled) windows 7...

Somehow, 
* even though I deleted the partition to reinstall windows, and I am 100% positive that there is no second windows install on the disk
* even though grub2 and grub0.97 both 'installed on the mbr'
* even though those two very reasons, still windows 'finds' its 'long lost brother' and gives the option to boot it...

If you ask me there is something very fishy going on but at least I now have windows 7, with one of my RAIDed disks in stead of a bright new computer that is not able to boot,

I will, for now, just stay with this option. I'm kinda 'out-installed' at the present moment, I'd like a os that I can actually use...

Oh, jsynesio, I made a separate /boot partition, both whilst reinstalling 9.10 alternate and 9.04 alternate, both didn't work out...

My hunch is that it either has something to do with windows7 being more agressively in the boot sector or grub can't handle RAID, even though it doesn't need to boot from it.

Beats me, but, well, I give up.

S.

ps: just to be clear: I installed windows 7 _before_ I reinstalled the alternate 9.04, still it goes directly to the windows dual boot screen

---


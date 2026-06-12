---
title: "Very dissapointed in Xubuntu"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by Roob on 2009-03-04
Since years I've been willing to try out Linux, but somehow it never really got so far, partly for being a bit deterred by stories about difficulties finding the right drivers etc. I learned that these days are over and now I finally got to the point of giving Xubuntu a try. I wished I hadn't! Installation seemed to go smooth, without any errors or warnings, but I wound up with a messed-up XP partition. Now I can't boot neither into Xubuntu nor WinXP [here ]("http://ubuntuforums.org/showthread.php?p=6835308#post6835308")for details).

I'm quite aware that the system (Pentium-3 on Abit BX133, 768 MB mem) I did the install on is not the newest anymore (end of 2000), and that the RAID complicates matters, but the BX133-board was quite populair at the time, so it's far from being obsolete. Xubuntu shouldn't have any problems with this system, especially as it is targeted at the older, slower systems - that's exactly why I chose this distro. 

Now it's one thing having troubles installing an OS, but the fact that Xubuntu messed up my WinXP-partition is, I think, inexcusable. I've been using computers since DOS, and installed allmost every Microsoft OS from 3.11 to WinXP, and usually ran into a fair amount of problems, but I never ever wound up with a messed up partition. Furthermore, I've been browsing through this forum intensively the last few days, and I noticed that I'm far from being the only one being unable to boot into either OS after trying to set up a Windows/(X)Ubuntu dual boot system (Although most problems seem less serious and are usually solved after some effort and the assistance of caljohnsmith).

This is not the way to go if you want a bigger market share (X)Ubuntu!

---

### Post by albandy on 2009-03-04
Did windows installer allow you to resize a partition? or install multiple operating systems?
Have you tried to boot from live cd and reinstall grub?
Or you windows fan, have you tried to boot with the windows Xp cd and use the repair console?
Do you know the commands fixboot and fixmbr of windows? I don't think so

---

### Post by Roob on 2009-03-04
> **albandy said:**
> Did windows installer allow you to resize a partition? or install multiple operating systems?
Have you tried to boot from live cd and reinstall grub?
Or you windows fan, have you tried to boot with the windows Xp cd and use the repair console?
Do you know the commands fixboot and fixmbr of windows? I don't think so

I tried most options you suggest, although for reinstalling grub I tried the Super Grub CD. For technical suggestions please go [here]("http://ubuntuforums.org/showthread.php?p=6835308#post6835308").

---

### Post by Roob on 2009-03-06
To get things clear: I'm not here to insult you guys and girls. Although I don't have much experience, I'm a big fan of Open-Source software: it's usually free, often better than its "closed source" rivals and last but not least: the source code is available. Furthermore the OS-es come in different flavors, so there's one for everyone and in general they demand less resources than their Microsoft or Apple siblings, and I assume they are "intrinsicly better" and safer. And of course it's charming to see you guys communicate in code on the internet. 

I just hope that somehow discussions like this can lead to better software/installers in the future. Because in all truth, I think less than 10% of my friends - a lot of them engineers - and none of my uncles, aunts, parents, etc would have succeeded in installing it if they had ran in the troubles I ran into. In stead they would have found themselves stuck with a broken system. And that's a shame because we all want to spread Open Source around (right?).

And yes, I am a bit frustrated and I feel the need for blowing of steam. Main reason I guess is that after reading reviews and posts on the net, I assumed it was going to be a piece of cake. Well: not in my case, and again: I'm not the only one.

[Yesterday I tried installing again]("http://ubuntuforums.org/showthread.php?p=6848406#post6848406") on an empty HD with three predefined partitions. How little did I know? I just couldn't get Ubuntu to install in the partition I created for it. I'm sure there is a good reason that the installer behaves the way it behaves and that it would have been possible somehow, and I could have managed with some study and effort. But certainly not the majority of my friends and family. Nothing beats how XP handles this in simplicity (don't know about Vista). So I think the installer could be improved here, and I think some additional advice/warnings should be added (defrag disk before proceeding, partitioning allways involves some risks, consider making an image of the existing OS before proceeding, ... -> see my first post in this thread).

One final note to leave you better humored after all this criticism: the LiveCD is awesome and left me very impressed. It's great to be able to boot from a CD and have a fully functioning OS at your disposal. Just one click, fill in the Web-key and BOOM you can browse the internet with (one of) the best browser(s) there is. In my case it came in very handy when XP couldn't find the driver for the network controller, and I'll take it whenever I'll be fixing a friend's system (hell, I might even use it for installing (X)Ubuntu on that system ;) )

If one of you find some time to spare to help me out with my install, please go [here]("http://ubuntuforums.org/showthread.php?p=6848406#post6848406"). I would appreciate it!

---

### Post by rapachooie on 2009-03-06
How did it mess up your windows partitions? 

By default, I think ubuntu (and its X and K counterparts) have a different resizing default in the install... it depends entirely on what your hardware setup is/was and how the partitions are allocated on the drive in terms of total size and available size.

In my many experiences of installing ubuntu and xubuntu and kubuntu (I keep reinstalling til Im happy), the default option is to resize the largest partition (generally the windows one)... I would venture to say you selected this option.

I personally prefer not to resize partions where possible because it involves the relocating data and updating... ALOT.  I think if something went wrong, it happened here.

Having said that, I have resized with the ubuntu system MANYYYYY times and have not had an issue.  I dont mean to lay blame but I think if something went wrong, its probably from your end.

In future (if you want to try reinstalling again), I recommend using the MANUAL option, and having complete control over what happens: I always like to resize my windows partition to the bare minimum with a little room for any installs I might need to do on Windows, and then set up 3 seperate partions in the available space remaining (after removing non-required partitions)... first partition I allocate X amount of space in an Ext3 partition and mount it as root (/)   secondly I allocate usually around 500MB-1GB and format it as SWAP (no mount required), then finally the remaining space gets Ext3 formatted and mounted as "/home".

I say all this becuse I think its important for Windows people to understand something about Linux, and that is that its UNIX-LIKE nature makes it much closer to Mac than to PC... Alot of people (myself originally included) feel that because they know "a thing or two" about Windows, then another OS like Linux could be no problem... but Linux needs alot of commitment on the newbies behalf to learn... even the Ubuntu based distributions still have features that are super-advanced and require heaps of knowledge to get the hang of! I still cant figure out how to do some of the simplest functions but that doesnt mean I give up on it or hate it for doing what it did... Having said that I have indeed been in your position and been angry at it for having done something wrong... right now I am attempting to troubleshoot 2 problems that persist but its all part of the learning process.

Finally, in terms of your system specs I would like to correct you on something... you mentioned that because the board was so popular it is far from obsolete? ANY board designed to handle a P3 is obsolete, doesnt matter if it was the mainstay of every computer enthusiasts arsenal... your computer is quite frankly ancient and I think its great that XP even ran on it, but if you give Xubuntu a try... your going to feel like your on the newest machine ever built (by comparison to XP in terms of system speed)... just dont expect the ride to be an easy one! 

Linux takes time and effort to learn.

Good luck!

Cheers

---

### Post by Roob on 2009-03-06
> **rapachooie said:**
> How did it mess up your windows partitions? 

That is a mistery to me. No resizing at all, [I installed Xubuntu on an empty HD]("http://ubuntuforums.org/showthread.php?t=1084528")!

> **rapachooie said:**
> ... but Linux needs alot of commitment on the newbies behalf to learn

I don't mind that, in fact I like messing 'round with computers and searching the net for solutions and learning new things. My problem is with the fairy tale singing 'round on the internet that all of this has changed with the introduction of Ubuntu.

> **rapachooie said:**
> (if you want to try  reinstalling again)

I'm certainly not giving up on (X)Ubuntu. In fact, I'm trying to reinstall right now. This is on a ("obsolete" ;) ) system of a friend. Then I'll try install it on the Asus Terminator of my parents which is terribly slow running on WinXP. And finally, I'm going to put a Linux distro, probably Ubuntu, on my own machine (QX6700 CPU on P5N32-E Sli).

> **rapachooie said:**
> ... but if you give Xubuntu a try... your going to feel like your on the newest machine ever built

I can't wait to see the results!.. Probably this weekend. Also curious how my friend is going to react, she's quite a computer illiterate and doesn't understand much of what I'm doing. She uses her computer for four things only: browsing, emailing, movies and playing Digger. As she allready uses Firefox and Thunderbird for the first two, the transition here will be small. She'll have to get used to a different movie player (now Zoom Player), which won't be very hard either. I found that it is even possible to get Digger to work in Linux. Her little daughter uses Office Word for text editing, but I reckon it'll take no time for her to control AbiWord better than she controls Word now (maybe I'll install OpenOffice as well if I/she don't like Abi).

---


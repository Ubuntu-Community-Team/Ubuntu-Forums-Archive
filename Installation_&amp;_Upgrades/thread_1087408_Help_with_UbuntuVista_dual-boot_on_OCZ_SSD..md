---
title: "Help with Ubuntu/Vista dual-boot on OCZ SSD."
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Nixie Pixel on 2009-03-05
First, I want to apologize in advance - my technical knowledge of hard disk drives is a limitation here, and I am hoping someone can help me understand in practical terms what I have to do.

I recently purchased a 60GB OCZ SSD to be my primary boot disk.  Ideally this disk would replace my current 80GB WD Raptor HDD as my Windows boot disk, a place to put the games that I want to be able to load super fast (the random access times really help here), and then put one or more of my existing Linux partitions, depending on which of them will benefit most.

The current generation of OCZ SSDs suffer from issues created by their JMicron controllers (which supposedly only have a 16kb cache, causing stuttering/delays when too many write commands are queued up).  I have read in a few places here that the ext3 (and, presumably, ext4?) journaling can exacerbate this problem.  I would like to avoid that if possible.

Currently I have swap, /, and a part of /home on half of my primary drive, with Windows and my games on the other half.  I will be keeping my Raptor as my second drive.  I want to put the programs/data that will benefit the most from the properties of the SSD on the SSD partitions, and put the programs/data that will benefit more from the properties of my Raptor HDD on the Raptor, while avoiding the stuttering/delay problem that has plagued JMicron controller-based SSDs.

The following thread in the OCZ forum explains ways that you can mitigate these problems:
[[COLOR="RoyalBlue"]OCZ SSD...What you need to know in (not-so) easy to understand format.[/COLOR]]("http://www.ocztechnologyforum.com/forum/showthread.php?t=50376")

Here is my problem - I don't understand a damn thing that was written in that thread.  I was lost rather quickly.  Apparently, how you partition the drive is important, but I don't know exactly what I should do, or how I should do it.  Should I partition the drive from a Windows or Linux utility, to avoid the problems indicated?  

If someone can help me understand what I need to do in order to get Vista and Ubuntu running smoothly on my new SSD, I would really appreciate it.

Thanks!

---

### Post by Nixie Pixel on 2009-03-05
By the way, if there is a plain-language note for noobs like me somewhere that can help, I would love that as well. 

Thanks!

---

### Post by hello_kitty on 2009-03-05
Apparently, it is important (under Windows) to properly align your partitions for optimal SSD read/write performance.  Click [here]("http://www.ocztechnologyforum.com/forum/showthread.php?t=48309") for the section of the OCZ forums that explains *how* to do that.  It seems simple enough, just download the recommended software and go from there.

I also have a SSD, but mine is a G.Skill Titan 128GB (the one with 2 JMicron controllers that eliminates stuttering) and I am not using Windows; rather straight Ubuntu 9.04, so I can't be of much help there.  Plus, I am deployed to the middle-east currently and do not have unlimited time on my hands.  ;)

---

### Post by Nixie Pixel on 2009-03-05
Thank you!

So what about Linux/Ubuntu?  What mount points will cause an issue if placed on an SSD with the controller issue, and what won't?  Can I avoid these problems, or should I just install all of Linux onto my Raptor?

---


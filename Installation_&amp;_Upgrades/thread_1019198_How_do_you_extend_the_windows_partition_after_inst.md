---
title: "How do you extend the windows partition after installing Ubuntu?"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by StarVoiceReason on 2008-12-22
Hello!  If there's anyone who can help, I'd really appreciate it!
So, I got a new computer, and I've hated windows for a long time, but there was never any alternative - I thought linux was only for people who really knew what they were doing, you know?
I have a friend who pointed out ubuntu to me a month ago, so I tried it and I loved it.
So, I dual installed ubuntu 8.10 on my new HP laptop that came with Vista - I do hate windows, but the laptop is a touch screen, and I want to play spore, so I kept Vista in its own partition.  I installed off the disc after I burned it, and I just took the recommended settings for the Vista partition - in this case 10%, something like 27 gbs.  
Afterwards, I opened ubuntu, saw that, yes, all the nifty touch screen/writing tablet reasons I bought the laptop for wouldn't work, and then tried to boot up windows.  It brought up the repair utility, complained about not having any restore points (what stupid f'ng system doesn't create one when it first turns on?????!) and then defaulted to ubuntu.  So I try again, it opens, but there isn't enough room to install anything on windows, much less spore & save a gb or so of word documents.
So I go to my packaged discs, and find that the disc that I thought was the restore disc for the OS is for office or some such nonsense.  The 'manage disc/partition' thing in windows (There are 4 partitions by the way; 2 windows - windows sys, win restore, 2 Ubuntu - one huge one, and another smaller one) can only shrink it's own partitions, and the computer won't LET me create a restore disc (It freaks out and cancels the process split seconds into it every time) through windows like it says I'm supposed to because they're too cheap to package one with the computer.  And the HP Site is convoluted and I can hardly FIND the 'order comp restore discs', much less actually get them to send them to me.
So, is it possible to somehow get ubuntu to shrink itself so I can give windows some breathing space?  If it wasn't for the touchscreen/writing tablet I would go straight to 100% Ubuntu, and screw microsoft; I've heard that you can get most stuff to work on ubuntu regardless of the 'proprietary vs opensource' bs.
So, yes, help!!!  Can I fix it?
-SVR

---

### Post by 73ckn797 on 2008-12-22
You can boot with the Ubuntu disk and run as trying out without installing. Go to System/Administration/Partition Editor.

There you click on the partition you want to change then you select the menu Partition/resize and can adjust the partition size to suit. You may have to unmount the drive first. That can be done by right clicking over the partition. A right click over the partition will *also *give even the resize selection.

Try it out.

---

### Post by StarVoiceReason on 2008-12-22
Okay, one more question.......  I've tried what you suggested, but there are like....  5 partitions there.  What is what???  Only the 'HP_Recovery' is labelled, and one of them has 2 separate subsections.  
1 - dev/sda 1 (NTFS), 
2 - dev/sda2 is recovery (NTFS), 
3 (5/6) - then there is 3 (extended), which contains 5(ext3) & 6(linux-swap), and 
? - one tiny unallocated.  
3 and 6 have key symbols.
1 & 2 are windows, right?
So, which are the linux ones I need to be changing?
-SVR

---

### Post by StarVoiceReason on 2008-12-22
Okay, So I looked around and finally decided 5 must be what I need to change, but.....  now how do I get that out of 3 so that I can use it for windows???

---

### Post by StarVoiceReason on 2008-12-23
Okay, I think I've got it.  I moved the free space to the front, behind the windows partition.  Will see if windows will see it after that.
Argh.  If I didn't write so much/love spore, you would be gone, foul OS.

---

### Post by 73ckn797 on 2008-12-23
> **StarVoiceReason said:**
> Okay, I think I've got it.  I moved the free space to the front, behind the windows partition.  Will see if windows will see it after that.
Argh.  If I didn't write so much/love spore, you would be gone, foul OS.


Once you have any extra disk space next to the ntfs partition, you will then resize the ntfs partition to use that space.

---


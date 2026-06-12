---
title: "delete recovery partition"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by loosescrew on 2009-08-21
Hello, I installed ubuntu within windows,@ 1 month ago. I like it. My question is - I have two drives within windows C:/ operating system,D:/ recovery partition. I created recovery cd when i first purchased comp. Can I safely delete the recovery partition and install ubuntu in it's place ? Will i be able to use the recovery cd's in place of the D:/ partition? Will the new install be ready to roll or are there drivers that i will have to install?         If so can you recommend a good partitioning tool to accomplish this. Thanks Joe

---

### Post by Soapy.Illusions on 2009-08-21
Hey loosescrew
 
I am not 100% sure you really want to delete that partition right now... just in case, but I know for my laptop that partition was like 3 gigs, really small.
 
You would probably be better to shrink your C drive and put it there

---

### Post by howefield on 2009-08-21
> **loosescrew said:**
> ...Can I safely delete the recovery partition and install ubuntu in it's place ? Will i be able to use the recovery cd's in place of the D:/ partition? Will the new install be ready to roll or are there drivers that i will have to install?

You really should read the manual that came with your pc, most are pretty simple and well documented in terms of recovering your system. In all likelyhood, you will be able to delete the recovery partition to use for other purposes, but do not do this lightly or without understanding how you get your machine back in the event of disaster, after all, you'll have gone from having two methods of recovery to one. 

What is the make/model of your PC ?

---

### Post by loosescrew on 2009-08-21
Thanks,soapy.illusions,howefield. Compaq presario s3100nx. That is my worry,I want to make sure that i can recover windows thru the recovery cd's before i attempt this. Soapy, Are you saying to shrink the windows C:/ drive ,then partition and install ubuntu? I'm looking thru the manual now. Thanks Joe

---

### Post by Mark Phelps on 2009-08-21
> **loosescrew said:**
>  ...  Can I safely delete the recovery partition and install ubuntu in it's place ? Will i be able to use the recovery cd's in place of the D:/ partition? Will the new install be ready to roll or are there drivers that i will have to install? 

The answer to all of these depends on how your OEM configured your machine to do recovery.  In some cases, all the recovery CD does is boot the machine into WinRE, which them looks for and uses a separate recovery partition on the hard drive which contains the actual recovery image.  In other cases, if it's a recovery DVD, or a set of CDs, the recovery image is copied to the disks and the partition is not needed.

The only way to be sure is to check with the provider of the machine; otherwise, if it's the first situation and you remove or otherwise tamper with the recovery partition, you won't be able to reinstall the OS.

---

### Post by loosescrew on 2009-08-21
I appreciate all the help. According to the comp manual you can recover the system with the recovery cd's. So I guess that question is answered. The reason i would like to do this is to save h/d space. Since i have installed ubuntu (within windows ) the windows o/s seems to freeze alot, especially when watching a video. I never had this problem before. Windows just seem to be unstable now. Joe

---

### Post by loosescrew on 2009-08-21
I have been doing alot of reading. It seems to me that my best option would be to install a second h/d. Does that sound reasonable?

---

### Post by Soapy.Illusions on 2009-08-21
IMO i think the most reasonable thing to do would be to shrink your current C drive, if you have space of course.

From Ubuntu you can access all your music and video files on your windows partition

Adding a second drive can be a pain, but if it is a possibility go for it

---

### Post by loosescrew on 2009-08-22
Thanks Soapy.Illusion. I removed as many unnecessary programs as i could and that helped. But I don't want memory to be a constant issue. So i ordered a h/d from newegg.I have been doing a great amount of reading so hopefully it will workout ok. I appreciate your help. Thanks Joe

---


---
title: "New to Ubuntu with some partitioning questions please"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by glen_luce on 2009-08-23
Hello all, 

I have searched the forums for my questions and being such a large and popular forum, I couldn't find any appropriate answers, so I apologise if I am doubling up.

I have been an "open source" user for a number of years, especially, Firefox, Thunderbird, Audacity, Open Office and Gimp, but all running on a Win XP Home operating system.

I have had the chance to briefly use Ubuntu 8.1 and 9.04 and I would like to use it as my new operating system for my new PC, finally breaking free from the MS shackles and running completely open source.

My new system is:


[LIST]
[*]AMD Athlon II 2.8 GHz Dual-Core
[*]Ausu motherboard M2N68-CM
[*]8Gb of RAM
[*]500 Gb HDD
[/LIST]
My questions are:

1. Upon installtion, whan creating a partition, do I need to create a SWAP partitian? Or is this amount of RAM sufficient to do without a separate SWAP partition?

2. I wish to separate the 500Gb HDD into a "system" partition and a "files" partition. This is what I am used to with Win XP. The "system" partition has tha OS and all the installed applications. The "files" partition is for all my documents. Does that mean that when I partition, I create:

sda/ - this is the root partition and where the "system" is installed, say 100Gb?
sda/ <other> this is for all my files, say 400 GB?

what selection should I choose for my <other>? home?

3. Am I understanding the partitioning procedure correctly?

4. Is 100Gb sufficient for Ubuntu? I do not use any large applications nor am I into gaming.


I appreciate your assistance.

---

### Post by junke1990 on 2009-08-23
you're system shouldnt be the prob, should run just fine

> **glen_luce said:**
> 
My questions are:

1. Upon installtion, whan creating a partition, do I need to create a SWAP partitian? Or is this amount of RAM sufficient to do without a separate SWAP partition?
** it is advised but I dont have one either.** 

2. I wish to separate the 500Gb HDD into a "system" partition and a "files" partition. This is what I am used to with Win XP. The "system" partition has tha OS and all the installed applications. The "files" partition is for all my documents. Does that mean that when I partition, I create:

sda/ - this is the root partition and where the "system" is installed, say 100Gb?
sda/ <other> this is for all my files, say 400 GB?

what selection should I choose for my <other>? home?
** I would split it up in 25B ext4 mounted as / and the rest as 475GB ext4 mounted as  /home**

3. Am I understanding the partitioning procedure correctly?
** as far as I can see yes, your settings will be saved in in your home folder too btw.**

4. Is 100Gb sufficient for Ubuntu? I do not use any large applications nor am I into gaming.
**mine is 20GB and I am a gamer**


---

### Post by junke1990 on 2009-08-23
btw the standard for swap is double the amount  of you're RAM, in your case that's 8 gb of ram but only 3.2 gb will be use if you use 32bit version. dont know how much it should be then. like I said I dont have one myself and I only have 2GBs of RAM.

---

### Post by ovroniil on 2009-08-24
1. As you have 500GB, so a partition of 3Gb swap will not do any harm. I strongly recommend to do the swap (for just in case).

2. In your case, "System" should be replaced by "/" (root) and "Files" should be replaced by "/home". Well... 100GB for root is a really extra large size!! 25GB space for root is more than enough! 

3. Upto now?? Yeah...

4. As I said earlier *"100GB for root is a really **extra** **large** size"*...:)

---

### Post by glen_luce on 2009-08-31
Thanks to you both for the information. You have confirmed I am on the right track.

I have decided to change my tact slightly, because I have many applications which may not run on Ubuntu. 

Plan B...

I want to run XP Home and Ubuntu on 2 separate partitions on the HDD.

1. Install XP home onto a 250Gb partition of the 500Gb HDD
2. Install Ubuntu on the second half.

My questions are:

1. My understanding is that when the Pc is booted up, I will receive and boot up menu asking which OS to load?

2. All my files, documents, images, music, videos etc are already stored on a 250GB external HDD so either OS should be able to "see" and access my external HDD, correct?

3. With this arrangement, the two OS's should work independantly and not interfere with each other?

Thanks again in advance.

---

### Post by raymondh on 2009-08-31
> **glen_luce said:**
> Thanks to you both for the information. You have confirmed I am on the right track.

I have decided to change my tact slightly, because I have many applications which may not run on Ubuntu. 

Plan B...

I want to run XP Home and Ubuntu on 2 separate partitions on the HDD.

1. Install XP home onto a 250Gb partition of the 500Gb HDD
2. Install Ubuntu on the second half.

My questions are:

1. My understanding is that when the Pc is booted up, I will receive and boot up menu asking which OS to load?

2. All my files, documents, images, music, videos etc are already stored on a 250GB external HDD so either OS should be able to "see" and access my external HDD, correct?

3. With this arrangement, the two OS's should work independantly and not interfere with each other?

Thanks again in advance.

How about:

Primary partition (100GB) - XP
Primary partition (300 + GB ) - NTFS format / For personal data and media
Extended partition
- logical (15GB) Ubuntu root (/); ext3 format
- logical (50GB)  /home; ext3 format
- logical (4GB) swap

*Ubuntu and windows can read/write into an NTFS format (your personal data/media partition)
*/home being separate from root means that if you have to reinstall ubuntu for any reason, you reformat just root whilst retaining your config files, settings, etc.
* swap at 4GB just because you have lots of space :)
* in case XP desires, you have 1 remaining primary partition left to put that so-called "recovery" partition.

For your other questions, yes, when you create a dual-boot scenario, you are given the choice which OS to boot into by GRUB (the Ubuntu preferred bootloader) .... and yes, each OS works independently from each other unless you decide to do a wubi-install.

Try out the liveCD and in live session (TRY WITHOUT CHANGES) to see how it works with your specs' and hardware (wifi, keyboard, F keys, etc)

Lastly, you can now use the external as a back-up storage for either OS.

Just my thoughts.

---


---
title: "do I need to re-install jaunty with different partition configuration?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Ascenti0n on 2009-04-26
I installed Jaunty yesterday on my second hdd which had overwritten Ubuntu & Kubuntu 8.10 partitions, which is what I wanted.

I wanted ext4 and a seperate .home partition.

I backed up my /home folder before install.

at install I was unsure which partition manager option to choose. In the end I opted for manual/advanced. I selected to delete all partitions from sdb and allocated the following:

(total hdd = 153gb)
first: /swap - primary - 3000mb (I have 2.8gb ram)
second: / - primary - 93.15gb
third: /home - logical - 57.45gb

first question: does the above look ok, ie the swap partiion is a primary partition, is it's allocated size big enough?

second question: does root partition always have bigger allocation than home?

All installed OK  but....

I made the mistake of restoring ALL my hidden files, rather than just the hidden program files. Now I get a permissions error about the use of $home.dmrc file must be 644. I can still log in and use the system, but I perhaps should have just used original 9.04 files and then installed my apps and restored the corresponding hidden app folder?

Third question: do I need to re-install the whole thing or is there a way to restore the original /home folders' hidden files?

Any help and advice will be very appreciated.
Thank you!

---

### Post by blackened on 2009-04-26
> **Ascenti0n said:**
> first question: does the above look ok, ie the swap partiion is a primary partition, is it's allocated size big enough?

With that much RAM you will likely never need more than 1GB of swap. You could even go so far as to limit the use of the swap partition in preference of RAM by editing your swappiness settings. Google has the answers.

> second question: does root partition always have bigger allocation than home?

If you want it to, then sure. Though typically, the root partition only holds the OS itself, as well as libraries and program files. Taking that into consideration, unless you install tons and tons of programs, then you will likely never need more than 20-30 GB. Personally I never allocate more than 10-15 GB to /.

/home, or other drives/partitions mounted somewhere in the filesystem, are where the bulk of your large files should reside.

---

### Post by GerMulvey on 2009-04-26
@ first question

swap is generally twice the physical ram in the system in your case 5.6Gb

/ I generally set to about 14Gb giving plenty of room. Size will depend on how many programs you are going to install. I don't think I have ever passed 8Gb to be honest. So I have room to spare if needed. So from 10Gb - 14Gb is likely to be more than ample. 
Leaving the rest of the space for /home

@ second 

no / just needs to be big enough for your system files/program files
/home can use the rest

@ third

I'm not sure on this one as I never needed to do this but hopefully your first two questions are answered!

---

### Post by Ascenti0n on 2009-04-26
thanks for the advise, you confirmed what I suspected, but I was not really sure.

Can anyone answer my third question 

AND 

can someone confirm if my primary and logical choices were correct?

---

### Post by theozzlives on 2009-04-26
I'd say:

First Primary - 20 GB for /
Second Primary - /home (whats left over)
Third Logical - /swap (amount of RAM)

You got 2.8 GB so multiply that by 1024 and that'll give the MB.
Don't re-install, just get your live CD and use Partition Editor to resize.

---

### Post by zvacet on 2009-04-26
Set swap as logical and for root I don´t think you will need more then 10 GB.There is no need to make that big swap.I will put something between 1-2GB.For third read [this.]("http://ubuntuforums.org/showthread.php?t=331855&highlight=%24HOME%2F.dmrc+file&page=2")

---

### Post by brandon88tube on 2009-04-26
Sorry, to be hopping in and stealing the thread, but I was wondering something very similar as to what you posted. I set up mine as / being 60gb logical and then my swap as 2gb logical as well. I'm not sure what would be the best setup so I will just list some specs to help out. I have 62gb of free space on my hard drive, 2gb of RAM and this is a laptop.

---

### Post by Ascenti0n on 2009-04-26
> **brandon88tube said:**
>  I set up mine as / being 60gb logical and then my swap as 2gb logical as well. I'm not sure what would be the best setup so I will just list some specs to help out. I have 62gb of free space on my hard drive, 2gb of RAM and this is a laptop.

I think the advice I have been given so far should help you.

I'm not sure / should be a logical partition, unless you are dual booting and have a Windows OS as your primary OS. But don't quote me ;)

---

### Post by zvacet on 2009-04-26
@ **brandon88tube**

You can install Ubuntu on logical partition but 60 GB for root is far to much.I believe that you installed on free space.Better solution is to install manual way and make separate home partition.In that case your root can be ~ 10 GB 1-2 for swap and rest for home.

---

### Post by brandon88tube on 2009-04-26
I've never done an install with a separate partition for my /home before. What is the reason for doing this? Also, is my swap size too small since I have a laptop? Thanks again for the advice you have given so far though.

EDIT: Forgot to mention that I am dual booting with Windows XP... can't get rid of it as I need some Windows only programs for work purposes.

---

### Post by zvacet on 2009-04-26
Reason for making separate home partition is that you can reinstall,fresh install and other things without losing your files and settings.I can not answer to your laptop related question.

---

### Post by brandon88tube on 2009-04-26
Well thanks for the reply.

---

### Post by sgosnell on 2009-04-27
You don't necessarily need swap space, unless you intend to use hibernate.  I don't hibernate, and I have no swap partition at all.  You can run out of RAM if you open a huge number of web pages and other programs at the same time, but I don't, and have no problems without a swap partition.  If you intend to use hibernate, you need to make the swap the size of your RAM.  Bigger than that is a waste of disk space, IMO, because it will never be used.

I just did a complete new install, and because my /home and / partitions are different, I lost nothing but some programs, which I easily reinstalled.  All my settings and data were intact, and Firefox wasn't affected at all - all my plugins, passwords, and everything stayed.

---


---
title: "Reinstall 8.10 on Vista"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by tacoma50 on 2009-03-24
I installed 8.10 on my laptop that already had Vista on it. I used a ubuntu 8.10 LiveCD for the install. I did a graphical guided install. The installed worked fine, I was able to boot to vista or ubuntu and both worked fine.

During the 8.10 install my HD partitions looked like this before ubuntu did any parttion work:
 /dev/sda1 = 96% (vista)
 /dev/sda2 =  3% (I assume this is my Vista recovery partition)
This is how I specified for ubuntu to create/resize partions:
 /dev/sda1 = 86%
 /dev/sda2 =  3%
 ubuntu    =  9%

Of course I played around with ubuntu(udates, installs, etc) and ubuntu will no longer boot, I can only boot to vista.

I would like to reinstall ubuntu onto the partition that was already created for it on the first install. I don't care if I lose any data on the ubunto partition. I don't want to lose data on vista partitions. I want to keep the bootloader that ubuntu 8.10 installed.

Can I just boot from my 8.10 CD again and install like I did the first time. When I get to the graphical partition window, should I then select MANUAL instead of guided?? Will I be able to select the already created ubuntu partition? Do I need to format it? Will it ask me to format or not?

I had tried this same thing a few weeks ago on another PC. On the first install I carved out 20gig from Vista for ubuntu, then when I reinstalled ubuntu, I had craved away another 20gig from vista. I had ended up with 2 two 20gig ubuntu partition, with only one being used.

help!!

---

### Post by tacoma50 on 2009-03-25
I've searched this forum and other places, but I have not found an answer to my questions. :(

Any help for this newb is greatly appreciated!!!

---

### Post by coffeecat on 2009-03-25
> **tacoma50 said:**
> ubuntu    =  9%

I guess you mean that about 9% of you HD has been formatted for use by Ubuntu. You'll find that there will be two partitions: the so-called root (/) partition (more-or-less equivalent to a Windows C: partition) which will be formatted with the Linux ext3 filesystem, and a swap partition of about 500MB - 1GB or so. Unlike Windows, Linux uses a dedicated swap partition.

> **tacoma50 said:**
> Can I just boot from my 8.10 CD again and install like I did the first time. When I get to the graphical partition window, should I then select MANUAL instead of guided?? Will I be able to select the already created ubuntu partition? Do I need to format it? Will it ask me to format or not?

Basically, yes, yes, yes, yes and ,er, yes. :p

Here's what to do. :wink: Boot up the live CD and go to System > Adminstration > Partition Editor. Make a note of what you find, but **don't do anything else**. There'll be sda1 and sda2 of course. Your ext3 root partitiion may be sda3, and the swap sda5. Or it may be sda3 and sda4, or something else. Simply make a note of what it is in your case.

Close the partition editor and start the installer. When you get to the partition stage, choose 'manual' or 'use existing partitions' or whatever sounds right. Tell the installer to create the root (it will be designated as /) partition on whichever partition it is already. It will pick up the swap partition automatically. OK all that and it will reformat your / partition, install Ubuntu and reinstall grub with a menu for dual-booting.

Good luck! :)

---

### Post by tacoma50 on 2009-03-25
Thanks CoffeeCat :) your instructions look easy. I will try tonight or over the weekend and report back with my results.

---

### Post by coffeecat on 2009-03-25
One other thought. Your Linux root partition is less than 10% of your total HD. That may be large enough, but I've already contributed to another thread today where two posters had root partitions in the 4GB size range and they had completely filled them up. You really need an absolute bare minimum of 6GB, more like 8-10, or even more for comfort. A default Ubuntu install takes about 2.5 GB, and a few extra apps will soon add another GB.

So, if you don't know what the root partition size is at the moment, when you start up the Partition Editor from the live CD, it will tell you. If you think it's too small, post back and we can look at that.

Also, I've only just noticed the last paragraph in your first post - the one about the other PC and the two 20G partitions. If you still want help with that, post some more details and we'll see what we can do.

---

### Post by tacoma50 on 2009-03-26
Coffeecat, 
My physical HD is 320gig, so 9% gives about 30g. So it looks like I should be OK with what you said. That is good to know for future refrence.  My other issue with the 2 20gig partitions has been resolved. Thanks:) 

> **coffeecat said:**
> One other thought. Your Linux root partition is less than 10% of your total HD. That may be large enough, but I've already contributed to another thread today where two posters had root partitions in the 4GB size range and they had completely filled them up. You really need an absolute bare minimum of 6GB, more like 8-10, or even more for comfort. A default Ubuntu install takes about 2.5 GB, and a few extra apps will soon add another GB.

So, if you don't know what the root partition size is at the moment, when you start up the Partition Editor from the live CD, it will tell you. If you think it's too small, post back and we can look at that.

Also, I've only just noticed the last paragraph in your first post - the one about the other PC and the two 20G partitions. If you still want help with that, post some more details and we'll see what we can do.

---


---
title: "OS not utilizing swap"
date: 2004-11-11
forum: Hardware &amp; Laptops
---

### Post by guyforget on 2004-11-11
I just noticed this last night, but my swap space isnt being utilized.  Its recognized by the OS, as I can check the disc structure with cfdisk and it shows the swap partition.  I have tried to use mkswap to get Ubuntu to start utilizing it, but nothing happens.  It doesnt throw any errors though, it looks like it takes the command, however when I check my mem usage the swap isnt being used.  My RAM (512MB) is being used at a fairly high rate.  Any suggestions?

---

### Post by randy on 2004-11-11
It's probably better that Ubuntu isn't using an swap.  When you start swapping memory to to disk your system will slow to a crawl.

---

### Post by ashley_v on 2004-11-11
That's good news.  I rarely use my swap and it's quite big so sometimes I make it smaller one sometimes no.  But I got lots of ram so it doesn't suprise me. Generally .deb packages tend to run very smoothly if their built right.

---

### Post by guyforget on 2004-11-11
[QUOTE=ashley_v]That's good news.  I rarely use my swap and it's quite big so sometimes I make it smaller one sometimes no.  But I got lots of ram so it doesn't suprise me. Generally .deb packages tend to run very smoothly if their built right.[/QUOTE]
 My RAM runs at nearly full usage with about 50% cached, which I realise isnt that bad.  Ive run Debian for some time, and have always used swapspace...

So, its obvious that the two posters above think that Ill be better off without swap space.  But, for my own knowledge Id still like to know how I would go about getting the OS working with it when mkswap doesnt work.  Anyone?  

Thx.

---

### Post by guyforget on 2004-11-11
[QUOTE=guyforget]My RAM runs at nearly full usage with about 50% cached, which I realise isnt that bad.  Ive run Debian for some time, and have always used swapspace...

So, its obvious that the two posters above think that Ill be better off without swap space.  But, for my own knowledge Id still like to know how I would go about getting the OS working with it when mkswap doesnt work.  Anyone?  

Thx.[/QUOTE]
 Eh, I got it.  

swapon

---

### Post by Julius on 2004-11-12
I don't really know how swap works, but I think swap will be used when the physical memory is not enough. I think 512 mb ram is enough and that's probably why your swap is not used in most of cases.

---

### Post by guyforget on 2004-11-12
[QUOTE=Julius]I don't really know how swap works, but I think swap will be used when the physical memory is not enough. I think 512 mb ram is enough and that's probably why your swap is not used in most of cases.[/QUOTE]
 No, no.  It wasnt being used because the OS didnt pick it up as swap at all.  Doing 'free -m' showed swap space as 0.0.  After doing 'swapon' it shows the proper 502MB of swapspace, which is now being utilized.  Then I added it to fstab.

---

### Post by TheCondor on 2005-02-07
Hello people

Im pretty new to Ubuntu and Ive been trying to understand why it uses so much swap space. Ive been using Suse 9.1 personal before I switched, and it never used the swap file. 

What Ive seen is this.

First of all, probably its kernel related ( correct me if Im wrong ) my RAM is recognised as 1GB, I actually have 1.5GB though. Ive been told to compile a kernel for my system but Im pretty clueless on how to do this, as Im not so experienced withlinux yet.

On to the swap problem, after having my system online for more than like 12 hours, the swap file is being used so much. In the beginning, it uses some 0-1MB only. The system is running pretty fast I must say. 

But after I go to bed, the next day the swap file usage reaches up to 200-300MB sometimes. Its currently at 30MB, but Ive seen it reach 300MB once or twice.

This seems pretty weird to me. My pc is a p4 2.6 with 1.5( 1 recognised )GB RAM, so I shouldnt be having such problems. Performance of the pc is kinda restored after playing a while with it, such as opening folders and programs and all, but why is the swap file getting used so much??

I also noticed that if I leave firefox running all day, it consumes some 150MB of my RAM, I saw that from gnome system monitor, and as soon as I close all the firefox windows, my swap usage is reduced. 

I really have no clue why this is happening, I think its not good though, judging from everything about how swap should be used in Linux. 

Id appreciate any help/suggestions on this, thanks in advance  :D 

P.S. Ubuntu OWNS  :D  :D  :D 

P.S. 2 ) I also noticed that on system monitor, under the devices tab, only my / and /home partition are listed, along with a tmpfs which is some 400MB. Shouldnt the swap partition be there as well?

---

### Post by jak on 2005-02-07
The default i386 kernel (i believe) only makes use of 900MB of RAM max. no matter how much you have. To make use of it you need to apt-get your cpu-specific kernel.
sudo apt-get install linux-686 for new Intel or AthlonXP
sudo apt-get install linux-k7 for any AMD Processors
sudo apt-get install linux-686-smp for Dual Intel Processors

I don't know about your swap space issues.

---

### Post by rufius on 2005-02-07
[QUOTE=guyforget]I just noticed this last night, but my swap space isnt being utilized.  Its recognized by the OS, as I can check the disc structure with cfdisk and it shows the swap partition.  I have tried to use mkswap to get Ubuntu to start utilizing it, but nothing happens.  It doesnt throw any errors though, it looks like it takes the command, however when I check my mem usage the swap isnt being used.  My RAM (512MB) is being used at a fairly high rate.  Any suggestions?[/QUOTE]
 To answer the swap question for all, the purpose of swap is the same as the idea in RAM. It is used to store information thats being worked on. But the key thing to remember is that swap is for storing these things, while RAM is being used dynamically by the processor. Think of it as the virtual memory that microsoft incorporates. As for TheCondor noting that his swap is growing up to 300 MB, thats a perfectly normal thing aside from any kind of hardware. As the system's uptime increases, you'll in turn end up using more swap because unused parts of the kernel will be stored in the swap. Also, programs that have had no activity for X amount of minutes will be partly stored in swap as time goes on. Also, if you've ever wondered why your ram is always being used, its actually being buffered and can be freed at will when you begin a process that may require a large amount of memory. Use of swap, memory, etc. is normal and should be embraced as a opposed to frowned upon. Don't let memory/swap use bug you ;) The kernel guys have it down. If any of you are interested in a more in depth description of how all this works, look into getting the O'Reilly book, Understanding The Linux Kernel.

---

### Post by TheCondor on 2005-02-07
Thanks for all the replies, I just got back home.

I apt-got the new kernel and Im ready to restart my pc. 

As for the swap concern. I said this because I heard that swap usage isnt something that should be done so excessively. All the people that I have asked told me that the swap file gets used when the amount of RAM isnt sufficient to hold the memory needed for the programs/functions of the pc, so the system starts writing this data to the swap partition, thus slowering down your pc's performance. 

I sure dont know enough about all this, as Im a n000bie, but please do correct me if Im wrong. I also said what I said about the swap file because neither in Mandrake, nor in Suse swap was used that much, no matter how much the pc needed the resources to carry out a certain process. It just seems weird to me thats all.

---

### Post by J77 on 2006-05-09
I'm having a similar problem to the OP...

I've got 4GB RAM and the kernal for the dual processors; when I set up ubuntu, I gave 10GB for swap (I do some heavy duty calculations) but have just noticed it's not being used...

I tried **swapon -a** but nothing happened...

Any ideas?

---

### Post by nocturn on 2006-05-09
[QUOTE=J77]I'm having a similar problem to the OP...

I've got 4GB RAM and the kernal for the dual processors; when I set up ubuntu, I gave 10GB for swap (I do some heavy duty calculations) but have just noticed it's not being used...

I tried **swapon -a** but nothing happened...

Any ideas?[/QUOTE]

Can you post the output of the free command?

---


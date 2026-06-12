---
title: "Need advice for new hardware for a server that will run VMWare server"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by caffienda on 2007-03-01
I'm looking to build a new server that will run VMWare server and multiple OS's.  These OS's aren't going to be CPU intensive.  What I'm trying to do is set up a "virtual corporate network" and practice some administration on various platforms. 

I have been out the IT industry for 2+ years, and have majorly (is that even a word??)  fallen behind on hardware.  My main sticking point here is MOBO/CPU.  
AMD or Intel? 
One CPU or Two? 
64 bit or 32 bit?

Here is what I *think* I want:

I already have 16 hard drives to choose from, so those are covered.  I'd like 2GB sticks of RAM, 2 to start with, than add 2 more later.. (but need to make sure they are compatible with the MOBO, and are ECC I guess)

Is it possible to run a Dual Processor MOBO, with only ONE CPU (then add one later)?
This is what I was thinking if I go with a Dual Processor AMD:
2  [AMD [COLOR="Blue"]Denmark 170's[/COLOR]]("http://www.newegg.com/Product/Product.asp?Item=N82E16819105030")
[ [COLOR="Blue"]SUPERMICRO H8DCE-O[/COLOR] ]("http://www.newegg.com/Product/Product.asp?Item=N82E16813182081")
Total:  [COLOR="Red"]$734.99[/COLOR]
Now what type of memory?
What is the difference between 939 and 940 sockets?

Now for the Intel..
[[COLOR="Blue"] Intel Core 2 Duo E6600 Conroe 2.4GHz[/COLOR]]("http://www.newegg.com/Product/Product.asp?Item=N82E16819115003")
[COLOR="Blue"][ ASUS P5WDG2-WS PRO]("http://www.newegg.com/Product/Product.asp?Item=N82E16813131039")[/COLOR]
Total [COLOR="Red"]$588.99[/COLOR]
Is the E6600 64bit?



I have also been looking at the Xenon CPU's that come in socket 604, 771 & 775!  This seems confusing! Then I have to figure out what kind of RAM I need (AMD uses 184 Pin, Intel needs 240 pin).  

I am open to suggestions here as to how to begin to look at this.  I have heard that the Opterons need massive amounts of power as well, which makes me lean towards an intel CPU.  

Boy, things have sure gotten complicated in computer hardware in the last 2-3 years!

---

### Post by zetaz7680 on 2007-03-01
Depending on the number of different virtual OS's you intend to run I would recommend that you get LOTS of RAM. At least 2GB. Also, an easy site to figure out the model/make of the RAM chip you need for whichever motherboard is [www.crucial.com](www.crucial.com) - you don't necessarily need to purchase it from there, but it will list out the compliant chip specs for you to shop elsewhere e.g. NewEgg.com

---

### Post by maniacmusician on 2007-03-01
I lightly skimmed your post and can give feedback on some parts of it without much research, so here you go:

1. The processor you chose is fine. I have an E6600, they are fast, reliable, everything that you'll ever need for a while. Yes, it does have 64bit capabilities.

2. I think you have the wrong concept about Dual Core computers; They are not 2 seperate CPUs. What happens is that there are two processor cores on ONE chip; essentially, this means that there are two processors in one CPU and it gives roughly twice the processing power of a single processor CPU of the same caliber. So, you cannot add one CPU and add one later. However, some advanced (and very expensive) hardware allows you to add multiple processors to your computer. For example, for servers, there are Intel Xeon-compatible boards, and some allow you to have two dual-core processors on them. So you can install one Xeon dual-core or 2 Xeon dual-cores; the latters would give you 4 processors spread over 2 CPUs for extreme computing power. However, I don't know if you need to take it that far; the E6600 may be enough for you. It's certainly more than adequate for desktop computing. Read up on it a little more.

3. your RAM choice is correct. I would start out with at least 2GBs of RAM, and add more RAM later as you add more virtual machines. 2GB sticks are pretty expensive, so you may want to go for 4 sticks of 1GB RAM instead; if you get a mobo that supports dual-channel RAM functions, you should see pretty good speed with that. If you're just going to be running servers in the virtual machines (aka no GUI virtual machines), then I don't think you'll need more than 4GB. If you're running multiple graphical virtual machines, then you may want to go for more, but there will be a sizable price difference.

4. For your VMing needs, I'd recommend VirtualBox. I'm pretty sure it can do everything you want out of a VM. Plus, it's open source. They have a channel on freenode; #vbox, I believe.

Overall summation; yes, go with Intel dual-core, plenty of RAM, use VirtualBox.

I can't speak on your mobo choices...that'd require extensive research depending on your specific needs.

---

### Post by afljafa on 2007-03-04
Re the AMD solution. I`m not sure the dual core opterons will go on the dual processor board.

I`m running a basic AMD semperon proc with a couple of Gig of ram. Happily running the host and a Linux/Windows XP guest inside.

---

### Post by jubxie on 2007-03-04
not sure of your budget, but just as a thought, the mac pro (not mac book) is $2500 with two dual core zeon chips and can take 16GB RAM. this thing is hugely upgradeable (could replace dual cores with quad cores!!) not sure how easy ubuntu is to install, I know people run it on mac books, I would guess the EFI is similar. from a strictly hardware standpoint, this thing is killer. though it might be a little pricy for a home project, but with a raptor hd and a few extra gigs RAM, this is as fast as they come.

---


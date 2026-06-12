---
title: "Difference between 32bit and 64bit?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by danill2008 on 2009-11-03
Hi,

Can someone please point me to know version is the best, 32bit or 64bit? and does 64bit also have the same features and run the same programs (e.g wine, crossover etc) like 32bit. If so, is 64bit faster than 32bit , like handling more RAM etc?

Thnx

---

### Post by jdeca57 on 2009-11-03
To answer as short as possible: if you have 3 GB internal memory or less use the 32-bit version. A lot (specially nonfree) of software is 32-bit, and many things remain easier. We're at a turning point, though. The answer won't be the same end next year, I'm sure.

---

### Post by NoaHall on 2009-11-03
The difference between 32 bit and 64 is the word size. It has a word size twice as large, so it can process data twice as big in the same amount of time. Example, if you had a word 128 bits big on a 32 bit computer, then it would have to be run through 4 times. On a 64 bit computer, it would only have to be run through twice. However, to you, a home user, the computer will only be slightly faster. It also allows support for more than 3.4GB of ram.

---

### Post by danill2008 on 2009-11-03
Thnx for info so far...so my best bet will be to stay with 32bit for now?
Also I have 4GB ram is there now way to utilise the full 4GB on 32bit, without installing 64bit?

---

### Post by anagor on 2009-11-03
Or to rephrase two previous posts, 
If you are asking then most probably you want to install 32bit version for now.

The 64bit will give you some improvements in stuff like large file compression, video encoding and program compilation.

However it will also give you headache with non-free components like Adobe Flash, many of the Windows programs will not work under WINE as smooth or as easy as they would under 32bit.

So at least for the next year or so, if you don't compress large files or compile huge programs on a daily basis, stay with 32bit. :)

---

### Post by anagor on 2009-11-03
Under 32bit memory addressing system, there is no way to access the full 4gb, not under windows not under linux :)

However, 4GB versus 3.4GB will not make any difference for a user.
For a server maybe, but for a desktop definitely not :)

---

### Post by realzippy on 2009-11-03
Interesting:

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by NoaHall on 2009-11-03
> **anagor said:**
> Under 32bit memory addressing system, there is no way to access the full 4gb, not under windows not under linux :)

However, 4GB versus 3.4GB will not make any difference for a user.
For a server maybe, but for a desktop definitely not :)

This isn't true. I believe since Karmic, Ubuntu 32 bit comes with PAE enabled. This means you can use up to 64 GB of RAM. If it isn't enabled, you can download the server kernel from the repos, which has it enabled. Thus, you can use all of your RAM. However, there are certain other limitations, and it doesn't work as fast as 64 bit.

---

### Post by anagor on 2009-11-03
NoaHall, you are right.

The server kernel is optimized for different load schemes, thus won't function at his best under desktop usage loads, if this what user wants.

But yet again, you are right. I totally forgot about PAE...

cheers;

---

### Post by danill2008 on 2009-11-03
Thnx to everyone who helped me:p
Looks like I will stick with 32bit ;)

---

### Post by howefield on 2009-11-03
> **danill2008 said:**
> Can someone please point me to know version is the best, 32bit or 64bit?

The question I'd ask is, if your hardware supports 64 bit, why wouldn't you use it ? And if you come up with a deal breaker, then you got your answer, if you don't then it's 64 bit all the way.

I saw this thread a little while ago and passed over it, but the closure announcement of the 64 bit forum made me come back to it. It says something when 64 bit has reached the stage where it is not treated as something different or special, but business as usual.

[http://ubuntuforums.org/announcement.php?f=&a=64](http://ubuntuforums.org/announcement.php?f=&a=64)

---

### Post by dhavalbbhatt on 2009-11-03
I have been using 64 bit since the days of 8.04 - almost 18 months now. I haven't found any major issues with using 64 bit, and especially since 8.10, things have been a lot stable. The question that you want to ask yourself is, why not 64 bit? If you find compelling reasons (like lack of software or hardware drivers, then sure, but I can assure you, most software runs on 64 bit these days) then sure stick with 32 bit, otherwise 64 bit is the way to go.

---

### Post by danill2008 on 2009-11-03
> **dhavalbbhatt said:**
> I have been using 64 bit since the days of 8.04 - almost 18 months now. I haven't found any major issues with using 64 bit, and especially since 8.10, things have been a lot stable. The question that you want to ask yourself is, why not 64 bit? If you find compelling reasons (like lack of software or hardware drivers, then sure, but I can assure you, most software runs on 64 bit these days) then sure stick with 32 bit, otherwise 64 bit is the way to go.

64bit sounds tempting, but the main reason I want to use 32bit is that im not sure if wine and crossover is stable under 64bit.

---

### Post by 1clue on 2009-11-03
> **anagor said:**
> Under 32bit memory addressing system, there is no way to access the full 4gb, not under windows not under linux :)

However, 4GB versus 3.4GB will not make any difference for a user.
For a server maybe, but for a desktop definitely not :)

This is false.

At work, we have a 32-bit CPU running non-enterprise Windows 2003 and using most of its 12g most of the time.  The desktop maybe can't access all of it (don't know about that) but certainly services can, and VMware has no trouble getting that RAM.

> 
[http://www.tuxradar.com/content/ubun...bit-benchmarks](http://www.tuxradar.com/content/ubun...bit-benchmarks)


I agree with most of what is said in this link.  I can only say that the differences SEEM to be larger, although time telescopes a bit maybe.  I had issues installing 32-bit Flash, but after installing the 64-bit version (which takes a bit of hoop jumping) it mostly seems to work fine.  64-bit flash is a beta at the moment, so it's a little flaky sometimes.  Usually it's fine though.

One thing I can say for sure:  If you compile a lot of C or C++ code (anything which uses "make") and you have an i7, having 64-bit and all those cores makes a stunning difference.  Use -j9 and then open your system monitor, and watch the CPU resources.  It helps if you run the thing through with -j1 or -j2 first, just to get a feeling of how much is going on.  Then run through with -j9 and start the timer.  I've seen all 8 "cores" above 80% for well over a minute at a time.

It just occurred to me that some people on an Ubuntu forum might not really get what I'm talking about here.  "Make" is a build tool that runs a compiler.  It can be threaded to take advantage of multiple processors.  You do that by saying, -jX where X is the number of cores you want to use, and typically you would give it X+1 for best performance.  Not sure I want to get into why it would totally take over the thread.

An i7 looks like 8 cores to the System Monitor, and probably to most of the software.  Effectively it is, but there are only 4 cores each of which have 2 hyper-threading modules.

I guess I'm diverging a bit.  IMO, if you have a 64-bit processor then you should put on a 64-bit OS or you just wasted your money.  I'm running 64-bit on my i7, and 6g RAM, and it kicks @$$.

No matter what might be missing now for the 64-bit desktop experience, there are mechanisms to run 32-bit apps right now, and as time goes by the need for 32-bit will dwindle to nothing.

You can hardly buy a 32-bit computer anymore.  The software vendors who don't see the point of 64-bit are soon to be out of business anyway.

---

### Post by howefield on 2009-11-04
> **1clue said:**
> This is false. At work, we have a 32-bit CPU running non-enterprise Windows 2003 and using most of its 12g most of the time.

What is false about it ?

I am most likely missing something, but aren't 32 bit operating systems which can address that amount of memory, in effect, actually running a 36 bit system ? It is the extra 4 bits which allow them to address more than 4gig of memory.

---

### Post by NoaHall on 2009-11-04
> **howefield said:**
> What is false about it ?

I am most likely missing something, but aren't 32 bit operating systems which can address that amount of memory, in effect, actually running a 36 bit system ? It is the extra 4 bits which allow them to address more than 4gig of memory.

Yes. Using PAE. Like I said. Windows server editions are the only windows ones which can do so.

---

### Post by dhavalbbhatt on 2009-11-04
> **danill2008 said:**
> 64bit sounds tempting, but the main reason I want to use 32bit is that im not sure if wine and crossover is stable under 64bit.

I don't use wine - so can't comment on that. However, I am sure there are others out there that use wine very regularly - maybe they can provide an answer. All I can say is, given the fact that wine is made for linux and other unix installations, it should be fairly stable under 64 bit as well. Besides, the fact that, there are other ways to make 32 bit software work in 64 bit. Just search for it in these forums and you will find plenty of answers on how to!

---

### Post by 1clue on 2009-11-04
> **howefield said:**
> What is false about it ?

I am most likely missing something, but aren't 32 bit operating systems which can address that amount of memory, in effect, actually running a 36 bit system ? It is the extra 4 bits which allow them to address more than 4gig of memory.

The 32-bit reference is the size of the data bus, not the address bus.  There have been paging schemes as long as I can remember for the memory access, and most of the recent ones work with very little fuss.  Back in the day when an Apple ][ was out, it was an 8-bit processor but had access to 64k worth of address space.  Or did you expect it to only be able to access 256 bytes of memory.

*Edit:*
As well, I somehow doubt that you can stick 2^64 words of memory on a 64-bit processor, so does that mean those chips aren't really 64-bit?

---

### Post by Dee.Rez on 2009-11-05
A few years ago, the 64 binaries just weren't as well maintained as the 32 bit ones. I'm guessing they are roughly on par now, but getting skype, flash and a few other things to run in a 64 bit enviroment isn't worth the modest performance increase - unless (as another poster pointed out) you intended to do some large file compressions or video editing.

---


---
title: "Ubuntu On my hardware (AND-Athlon-64)"
date: 2010-09-23
forum: Hardware
---

### Post by OperatorA on 2010-09-23
Good morning all you friendly Ubuntu "geeks" out there. I have a hardware/OS question.

I have a 5 year old eMachines (W3410) system with a --

ADM Athlon 64 CPU.
ATI-Radeon-Xpress 200 video card (uses 128MB of system RAM)
100 GB hard drive
1MB of RAM ***upgrading*** to the max allowed of 2MB.
DVD-R/RW
Digital card reader.

Right now I am dual booting Windows XP & Ubuntu-Linux.

I am considering going to the Ubuntu AMD-64 version as a stand alone and killing Windows. Do y'all think I have a good enough hardware set to run the 64 bit version of Linux?

Thanks...
Larry.

---

### Post by cascade9 on 2010-09-23
Minor typo, you meant 1GB, upgrading to 2GB. 

That shoukld run 64-bit just fine. 1GB is borderline as far as RAM goes for 64-bit IMO, but with 2GB, that should be all good ;)

---

### Post by PresenceofMind on 2010-09-23
Have you had any issues with your current setup whilst running Ubuntu/Windows? If not then a Linux-only machine is a good option...

And if you are going 64-bit, a minimum 4GB RAM upgrade will be more healthy for your system. 64-bit OS and 64-bit software consumes more system resources especially the RAM. 

If you wish to run a standalone Ubuntu system with 2GB RAM then a 32-bit OS will run just fine.

---

### Post by cascade9 on 2010-09-23
> **PresenceofMind said:**
> And if you are going 64-bit, a minimum 4GB RAM upgrade will be more healthy for your system. 64-bit OS and 64-bit software consumes more system resources especially the RAM. 

If you wish to run a standalone Ubuntu system with 2GB RAM then a 32-bit OS will run just fine.

You dont NEED 4GB+ to make use of 64-bit. Even on older linux versions with 2GB, 64-bit does show improvments all across the board- 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

I was using 64-bit on a 2GB system for over a year, no issues at all. ;) 

True, 32-bit will run 2GB just fine...but for that matter, it will run 4GB, or even more 'just fine' ;) If you've got a 64-bit capable system, why not use it?

---

### Post by PresenceofMind on 2010-09-23
> You dont NEED 4GB+ to make use of 64-bit. Even on older linux versions with 2GB, 64-bit does show improvments all across the board

In fact, any system with even 1GB of RAM 'can make use of 64-bit' (yes, just like you said..). It will just run as though you have a 512MB RAM (which for linux is still a lot). I never said you NEED to have 4GB RAM..... it was more of an incentive, since 4GB RAM is becoming a standard among many consumer PCs, and it's ALWAYS GOOD to have lots of RAM.

> True, 32-bit will run 2GB just fine...but for that matter, it will run 4GB, or even more 'just fine'

I'm afraid it's not as smooth as you might think. Most of the time 32-bit systems detect only around 3.something GB of RAM even if you have just put in 4GB of RAM. You NEED work arounds like the PAE before the system "sees" 4 Gigabytes of RAM.

So, although it will run, you won't be able to make use of all of the 4 gigs and to me that's just wasting resources which is...well a waste really....

You can read more about the 3GB barrier and how to break this using PAE here:

[http://en.wikipedia.org/wiki/3_GB_barrier](http://en.wikipedia.org/wiki/3_GB_barrier)
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

>  If you've got a 64-bit capable system, why not use it?

Of course, you'd want to use it :D...but you'd also want to enjoy using it :P Things like Compiz, firefox etc uses a lot of RAM. 

In fact, read this forum. It shows you the likely danger of running a 64-bit system using 2GB RAM (OS: Ubuntu 10.04 LTS)

[http://ubuntuforums.org/showthread.php?t=1480178](http://ubuntuforums.org/showthread.php?t=1480178)

---

### Post by cascade9 on 2010-09-23
> **PresenceofMind said:**
> In fact, any system with even 1GB of RAM 'can make use of 64-bit' (yes, just like you said..). It will just run as though you have a 512MB RAM (which for linux is still a lot). I never said you NEED to have 4GB RAM..... it was more of an incentive, since 4GB RAM is becoming a standard among many consumer PCs, and it's ALWAYS GOOD to have lots of RAM.

1GB will run as though you have 512MB? You not using the old '64-bit is twice as big so therefore it will use twice as much RAM' myth are you? 

64-bit will use more RAM, but its nowhere near 2 x the RAM use. 

True, you never said you need 4GB...but then you also seem to have missed the OPs "2GB RAM limit". 

> **PresenceofMind said:**
> 
I'm afraid it's not as smooth as you might think. Most of the time 32-bit systems detect only around 3.something GB of RAM even if you have just put in 4GB of RAM. You NEED work arounds like the PAE before the system "sees" 4 Gigabytes of RAM.

So, although it will run, you won't be able to make use of all of the 4 gigs and to me that's just wasting resources which is...well a waste really....

You can read more about the 3GB barrier and how to break this using PAE here:

[http://en.wikipedia.org/wiki/3_GB_barrier](http://en.wikipedia.org/wiki/3_GB_barrier)

IIRC, doesnt ubuntu automatically use PAE if it detects 4GB or more of RAM? Even if it doesn't enabling  a PAE kernel is really easy. 

> **PresenceofMind said:**
> Of course, you'd want to use it :D...but you'd also want to enjoy using it :P Things like Compiz, firefox etc uses a lot of RAM. 

In fact, read this forum. It shows you the likely danger of running a 64-bit system using 2GB RAM (OS: Ubuntu 10.04 LTS)

[http://ubuntuforums.org/showthread.php?t=1480178](http://ubuntuforums.org/showthread.php?t=1480178)

Compiz, I dont ever use. Kwin is running here though, and was on my 2GB 64-bit system. Even with kwin, and my nasty habit of opening 25+ tabs in firefox, I never saw over 750MB used. The only times I ever cracked 1GB of RAM use was with video ripping and heavy mutlitasking (like firefox with 25+ tabs open, exaile, duluge, ark, ocular and a couple of dolphin instances open). Right now, with 25+ firefox tabs open, I'm using 480MB total. I'm using an linux distro with a bit less 'cruft' than ubuntu though ;) 

BTW, that thread you linked didnt really have much, just somebody complainign about using more than 1GB of RAM (original picute posted gone, but the next poster said they were using 822MB) and somebody else using 1.5GB from htop with nearly 500MB free. I dont see anything dangerous there.....

---

### Post by PresenceofMind on 2010-09-23
Excuse my ranting.... a 2GB upgrade would be a no brainer then, in which case all the arguments presented by me becomes void. 

My final thought then is this:

Yes, you have the hardware to run a 64-bit Linux OS (based on your description), but those are minimum. So if there are any performance gains to be expected, they will be minimal (or none at all).

---

### Post by OperatorA on 2010-09-23
All the discussion above...re RAM...My eMachines W3410 can only HOLD 2-MB of RAM. (2 * 1MB) is all the Motherboard will support.

As I am a "Po' Boy" I have to go with that. It was a stretch for me on my income to get the 2MB I ordered from "Tiger Direct" today. Supposed to be here Monday the 27th. I can't afford a new PC at this time and I do NOT like Win-Vista or Win-7. 

I do like Windows-XP which I have dual booted with Ubuntu 10.4 LTS. I also like Ubuntu VERY MUCH. I have to dual boot because the rest of my family are not too bright when it comes to computers...Wifey has Windows-XP on "our" (yea...right...)Dell Inspiron 1000 laptop. she is just now learning that. (Windows-XP)

SO some of you say with an AMD-Athlon-64 and 2MB of RAM I SHOULD load 64byte Ubuntu and some say NOT.

I think I will stay "static" in my dual boot for now and see how it all runs with 2MB of RAM. I run 1MB at the moment and it came with 512MB of ram. I added the 2nd 512MB last year.

I can pass on both of my 512MB sticks to friends to help them upgrade their 512MB systems to 1MB. 

Thank you one and all for the feedback...
LArry

---

### Post by eotakos on 2010-09-23
> **cascade9 said:**
> You dont NEED 4GB+ to make use of 64-bit. 
I was using 64-bit on a 2GB system for over a year, no issues at all. ;) 


+1 !  

I have been using a 3.5 year-old pc with 2GB for 2 years with 8.04 64bit, and now I have installed 10.04 64bit... no regrets!

---

### Post by OperatorA on 2010-09-23
I don't regret installing the 32-bit Ubuntu. I really like it. I will continue to dual-boot until i am as comfortable with it as I am with windows-XP then i'll have a funeral for W-XP and wipe and go Ubuntu all the way...

I am tired of Micro-stupid making functioning equipment obsolete just because they think this "Po-Boy" needs to buy a new computer with their latest OS on it. 

I live on a limited income and I don't have the extra $600 for a new computer every 3-4 years. My late mother Ruth (passed on 12-30-09) bought this computer for me as a birthday present when I turned 50. I will keep and run it until it mechanically dies of old age...Linux will help me do that.

I really think Ubuntu-Linux is amazing. Clean interface..fast on my hardware. Next week after I install the 2MB of ram I have on order it will be even quicker.

NOW...is it just my imagination or does Ubuntu resemble the Apple OSs a little bit? I an not familiar with Apple except what I have seen in books and magazines...

Larry (ex COBOL programmer)

---

### Post by esunday on 2010-09-23
> **PresenceofMind said:**
> Have you had any issues with your current setup whilst running Ubuntu/Windows? If not then a Linux-only machine is a good option...

And if you are going 64-bit, a minimum 4GB RAM upgrade will be more healthy for your system. 64-bit OS and 64-bit software consumes more system resources especially the RAM. 

If you wish to run a standalone Ubuntu system with 2GB RAM then a 32-bit OS will run just fine.


Well, I might just be an old codger, but I've been running an Athlon 64 with the 64 bit Ubuntu for 2 years, with just 500 MB  ( .5 GB) of RAM, and it runs just super.  Of course, I'd like more RAM, but I get by.  The only performance hit is when I'm runing intensive apps like torrent downloads, then it does take a bit to get other apps running, or to switch from app to app.  But I don't get any crashes, a testimony to Linux I guess ....:guitar:

---

### Post by cascade9 on 2010-09-24
@ esunday- I normally take linux crashing as a sign that the hardware is sick.  

> **PresenceofMind said:**
> Excuse my ranting.... 

If that is 'ranting' you are much nicer, or calmer, or both, than I am. ;) 

> **OperatorA said:**
> SO some of you say with an AMD-Athlon-64 and 2MB of RAM I SHOULD load 64byte Ubuntu and some say NOT.

Ywah, well, that is what can happen. There isn't always a 'correct' answer with things like 32bit vs 64bit. Good luck with your 32bit OS, I hope you enjoy, and hopefully somebody drops a nice big bundle of money on your lap. :)

---

### Post by esunday on 2010-09-24
I'd say do it, then you're taking best advantage of the processor at least.

And like I said, I'm doing fine on 500 MB of RAM.  I multitask all over, and no problems

---

### Post by OperatorA on 2010-09-24
Well with an AMD-Athlon-64(3200) and 2MB of RAM this old box on Ubuntu-Linux should do just fine. 

Next time I work some overtime I will buy a 16MB thumb drive to backup the "My Documents" folder to and start playing with both a full-install of 32-bit, then 64-bit, maybe do a dual boot with Ubuntu and another flavor of Linux. (is that possible?)

I am definitely over Microsoft. I can't afford a new "Apple" and Ubuntu gives me an alternative to Microsoft.

Personally I have been in Mainframe Computers (IBM big-iron)from 1974 to 1999

I've had a PC of one form or another since MS-Dos 6.22 / Win-3.11 days. My 1st computer was a Salvation Army Thrift Store special...IBM PS/2-50. i-286 and a 10MB hard drive - monochrome monitor, came with DOS.3 which I upgraded to DOS.6-22.

Had MS-DOS 6.22/Win3.11, Win-95(OSR-1&2), Win-98(OSR-2), Win-Me, Win-XP(SPs 1-3).

Ubuntu is just another delicious flavor in the OS world for me and not a scary one! I LIKE IT!...you Forum people are all so informative and quick to answer my questions...thank you one and all!

Yours in computing
Larry

> **cascade9 said:**
> @ esunday- I normally take linux crashing as a sign that the hardware is sick.  



If that is 'ranting' you are much nicer, or calmer, or both, than I am. ;) 



Ywah, well, that is what can happen. There isn't always a 'correct' answer with things like 32bit vs 64bit. Good luck with your 32bit OS, I hope you enjoy, and hopefully somebody drops a nice big bundle of money on your lap. :)

---


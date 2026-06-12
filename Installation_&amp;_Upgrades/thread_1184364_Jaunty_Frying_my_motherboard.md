---
title: "Jaunty Frying my motherboard????"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by ceejay on 2009-06-11
Hello - I have to say this sounds a bit odd but it's what I'm seeing so here goes ... I had 8.04 running on a home-made machine built around an Intel DG965WH (Core2Duo) motherboard. It was ok but I had some issues with browsing so thought I'd try an upgrade to see if it resolved them (as an aside - it looks as though it has!).

As its a homemade box, I thought it a good idea to monitor temperature so have set up the sensors-applet gadget in my desktop panel, monitoring the CPUs and two of my discs.

So I upgraded initially to 8.10 and straightaway noticed that the CPU temperatures were much higher than I was used to seeing: previously they had been in the 40s or occasionally 50s when pushed. Now they were going up into the 60s and 70s. Carrying on with the upgrade into 9.04 this has continued: if I let it alone, the temperature on both cores is going well into the 70s, which is not sustainable, I think.

CPU usage is 100% on both cores: if I throttle it back by stopping tracker-indexer then the temperature drops back to around 50.

This is not an ambient temperature problem - the disc temperatures are behaving as before, around 40.

What seems really odd is that I have regularly pushed the CPUs to 100% before - I often use this box for processing video files - and have never seen the temp go over 70.  So what's going on?

1 - as a short term fix, what's the easiest way to stop tracker-indexer from running up each time I start?

2 - is it possible that a change in the OS has affected the way that fans for example are being controlled?

3 - is it possible that the temperature readings are not correct?

Any clues much appreciated.

THX.

---

### Post by donato roque on 2009-06-11
This is not a solution per se but I encountered the same problem
right after I upgraded to a fresh install of Jaunty.  The culprit
here is the runaway tracker-indexer especially in the first minutes
after boot.  My solution was to purge tracker and replaced it with
beagle.  I "heard" that beagle has its own issues too, so I'd 
keep an eye on the processes for about a week.  It's ok now.
No hyperactive processes or overworked cpu's.

---

### Post by ceejay on 2009-06-11
Thanks.  I have disabled (rather than uninstalled) tracker - not installed beagle or anything else because TBH my use of the desktop is fairly light (this is more of a server that I happen to want to interact with from time to time).

I'm still puzzled about the temperature thing, though, and I'm now nervous about working it hard...

Any other thoughts out there?

---

### Post by ceejay on 2009-06-14
So, disabling tracker has at least allowed me to keen the machine turned on and perform one of its functions - file serving, which is undemanding on the CPUs.

But the other thing I want to do is to crunch video files, and sure enough every time I give it some real work to do the core temperature shoots up to 70C or more.

This is definitely hotter than it ran under 8.04.

Any suggestions? I am guessing that the fans are no longer being controlled as they used to be?

Help much appreciated before I find myself having to do something drastic...

TIA

---

### Post by wpshooter on 2009-06-14
Have you tried monitoring your temperatures with Xsensor instead of sensor-applet ?

---

### Post by ceejay on 2009-06-14
Well, I just tried Xsensors and got the blank screen that others have reported ... but in any case, as I understand it, this is just another UI to sensors ... if I run that from the command line, I get the same temperatures as are being shown to me by sensor-applet, which I guess isn't surprising if they are just different interfaces to the same underlying sensors.  SO even if I do persuade XSensors to talk to me, its just going to give the same numbers?

Any other ideas as to why I'm running so much hotter than before I upgraded?

TIA

---

### Post by wpshooter on 2009-06-14
Ceejay:

         Have you checked the monitoring, fans, etc. related parameters in your BIOS ?

         I am now running Jaunty on the machine I am typing this on and I was previously using most of the other previous Ubuntu versions on and if anything Xsensors shows the CPU and M/B temperatures lower than when running previous versions of Ubuntu !!!

---

### Post by ceejay on 2009-06-15
Hi

thanks for the response. Yes, I've had a look in the BIOS - there isn't a lot to play with there, but it seems to be correctly set up. I have made a few changes to see what happens but no obvious effect.

What is really striking me is the very obvious and immediate change in temperatures as I went from 8.04 to 8.10 (as an intermediate step to 9.04). I'm wondering whether its a specific issue with my motherboard (Intel DG965WH) ... in which case it might take me a while before I find someone else with the same setup!

Thanks
Ceejay

---

### Post by wpshooter on 2009-06-15
Did I ask if your BIOS is on the latest and greatest version ?

---

### Post by ceejay on 2009-06-15
No, I don't think you did ask if I had the latest BIOS ... but if you had, it would have been a good question, thanks for reminding me!

I had a look and sure enough there is a significantly newer BIOS. As always the release notes don't list anything that exactly matches, but there is something just close enough to make you think its worth a try!

So I have now updated the BIOS to the latest and greatest ... and its made precisely no difference.

More ideas?

ATM I've got a box which I don't feel at all confident about leaving running overnight running intensive rendering batch jobs, which I would like to be able to do!!

TIA
Ceejay

---

### Post by AoSteve on 2009-06-15
I thought I'd just pop in and tell you of a little experience I had with my friends first Core2Duo..   

He got a nice little box picked and we ordered the stuff off of newegg.  We got the system all built, with the OEM heatsink..   Windows Vista Home Premium installed and ready to play.  

I install "SystemFan" an application for sensor monitoring on windows.  He started playing with it and the normal temperatures ran from 35-50C ranging on how hard he pushed it.   Well, I watched long enough and said it was time for Orthos.   Sure enough that processor hit 70C and I was worried.   That's just too hot.

I modified the heatsink that came with the process (retail E4400) and used some artic silver 3 for the thermal grease.  After all of that, it ran about 10C cooler and never thought about getting over 60C much.  :)

---

### Post by ceejay on 2009-06-15
Hi AoSteve

Indeed, my thoughts are turning to the heatsink/CPU coupling, I may go and get some stuff tomorrow.

The other thing I notice is that the fan at the back of the case, although running, is running very slowly ... I would have hoped that some part of the system would be reacting to high temperatures and turning it up to hurricane force but no, it is just idling away, hardly pushing air out the box at all.

I don't really understand the mechanisms that ought to be at work here, but I can imagine that something might be broken by an upgrade.  Improving the heat sinking, although a generally good idea, can't be the whole answer.

Ceejay

---

### Post by AoSteve on 2009-06-15
Well, take this example to heart.   As operating systems with Microsoft got newer, the ability to use the processors better grew.  This leads to more heat in any sense.  A good example is in fact a stock Pentium 3 450mhz system that I had.  In windows 98, I'd hold an average of 50C  (which wasn't bad for those processors as much heat as those Katmai cores pushed out).  I went to Windows 2000 with the SAME setup, and during usage of the processor, it got hotter.  But there was noticeable increases in performance in things as well, specially with burning CD's or encoding MP3's.   This may be your case.

When I first got my Pentium 3, I took the heatsink off first thing.  There was a "thermal pad" on the stock heatsink transfering the heat to the heatsink.  With this setup, I saw temperatures reach over 60C in normal operation!!!   So, I downloaded a program to help synch the idle for the processor and it helped when the processor was idling, but not at full bore.    

When my (newegg rocked then, and still does) package of a heatsink, fan, and artic silver came in I quickly installed the setup.   I never saw temperatures over 55C again.

So, this could be a good bit of your problem.   If anything, I'd look for some Artic Silver.  I've been using it for years and you couldn't get me to change.   If this stuff will last for 6 years on a heavily overclocked AMD Athlon Thunderbird setup, it's good.  :)

---

### Post by ceejay on 2009-06-16
At this point I started following another direction. I found some other similar threads including  [http://ubuntuforums.org/showthread.php?t=1186622](http://ubuntuforums.org/showthread.php?t=1186622) which led me to a long discussion about DSDT files, I come in at post number 102 ... [http://ubuntuforums.org/showpost.php?p=7464970&postcount=102](http://ubuntuforums.org/showpost.php?p=7464970&postcount=102)

Still unresolved at this time. Am I caught between a possible kernel bug and some undesireable BIOS behaviour?  Will applying some magic paste be enough to keep my system working? Will I give up on Ubuntu altogether?

Hmmm, tricky.  But if anyone reading this has a bright idea, please do chip in.

Ceejay

---

### Post by ceejay on 2009-06-17
OK, I have an update in case anyone is reading this ... the problem seems to be in the kernel.  If I downgrade to the Hardy kernel (2.6.24-16-generic) then the core temperatures at idle immediately drop by about 15C.

I also tried Intrepid (2.6.27-7-generic) but as expected this behaves in the same (hot) way as Jaunty (2.6.28-11-generic).

So the "fix" was simply to move the Hardy kernel to the top of the grub boot list and reboot!

As it happens the browser problem which was the reason for me upgrading in the first place still seems to be fixed with this combo, so I guess I'm happy.

Thanks
Ceejay

PS: see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264290](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264290)

---


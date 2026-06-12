---
title: "ASUS M4A78T-E Freezes with 9.04"
date: 2009-10-03
forum: Hardware
---

### Post by HighlyDubious on 2009-10-03
[FONT=Tahoma][SIZE=2]I'm having trouble installing Ubuntu 9.04 (x64) on a new system I'm building.

Specs are:
[/SIZE][/FONT]  
[LIST]
[*][FONT=Tahoma][SIZE=2]Mobo: ASUS M4A78T-E [/SIZE][/FONT][FONT=Tahoma][SIZE=2] (BIOS v2105)[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]CPU:    AMD Phenom II X4 965 3.4Ghz[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]GPU:    ATI 4650 (OEM Generic)[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]     RAM:  8GB (4x2GB) Corsair CMX4GX3M2A1600C9 (DDR3 1600 CAS 9)[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]HD:       500GB Maxtor (SATA)[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]CD: TSST Corp CD/DVD RW SH-S204N (SATA)
[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]     PSU:    750 Watts (Generic)[/SIZE][/FONT]
[/LIST]
[FONT=Tahoma][SIZE=2]I posted before on this topic ([here]("http://ubuntuforums.org/showthread.php?t=1280783")), but either it got buried under the flood of newer messages, or I was too verbose in my post, so I'll keep this simple.

The system is working perfectly under Windows 7 & XP (both are x64). I've tried 6 times to install variants of Ubuntu (x64), and each time the machine froze at some random point during the installation. Even just running from the Live-CD I've had programs and processes randomly crash.

And no, I'm not trying to use the proprietary ATI drivers.

Does anyone know of incompatibilities between this motherboard board and Ubuntu/Xubuntu/Kubuntu/etc? Or, perhaps  known problems with the [/SIZE][/FONT][FONT=Tahoma][SIZE=2][COLOR=black][SIZE=2]AMD 790GX/SB750  chipset that the mobo is based on?

All advice and tips  on how to get this working will be appreciated.

P.S. Even if you don't know the answer to help me, please check the parts of the poll which apply to you. Maybe the aggregate info from the poll will tell me something useful about the Mobo or chipset.

[/SIZE][/COLOR][/SIZE][/FONT]

---

### Post by HighlyDubious on 2009-10-18
bump

Just to update, I've tried installing the 9.10 beta, but experienced the same random locking up during the install process.

After several attempts, I was able to get Xubuntu 9.04 to fully install. But once installed, it also had random crashes. 

For example, things like the System Monitor, or Firefox, or a terminal window just suddenly stopping/closing for no obvious reason. Or other times X resets and dumps me back at the log-in screen. These things happen even if the machine is just sitting there and has not been touched for several minutes. It's totally random, and totally weird.

For what it's worth, I've run Memtest86+ v4.0 for 3 full cycles, and I've also run Prime95 (under XP and Windows 7) for over 30 mins. This tells me that my RAM is good, and that the CPU is not crashing due to heat or flakiness. Everything I can test under Windows XP and Win 7 tells me that the memory, CPU, and mobo are completely stable and solid. But when I try to run Ubuntu, I get weirdness every time.

Earlier today I did successfully install PCLOS (I had the disk laying around from a prior install on another machine). But that is x32 only, and if there's any way possible I'd prefer to not lose more than half of my 8GB of memory by going down to x32. I'd also prefer to not be forced to another distro if I can avoid it. It's hard enough to learn the in's and out's of Ubuntu. Trying to learn the quirks of another distro is simply not appealing. 

If it turns out that this mobo and this BIOS are just flat out not going to work with Ubuntu, then I'll probably buy a new mobo.
[COLOR=Magenta][B]
With that in mind, I'm asking for comments from ANYONE who is currently using any x64 variant of Ubuntu/Kubuntu/Xubuntu/etc with any AM3/DDR3 mobo. (Yes, I know that AM2+ is compatible with AM3, but I'm really only interested in mobo's that are truly AM3/DDR3)[/B][/COLOR]

So, if you are **successfully** running any x64 variant of Ubuntu on an AM3/DDR3 mobo, please just leave a comment here telling the mobo mfg and model. Or, if you are having problems running x64 Ubuntu on an AM3/DDR3 mobo, let me know that as well, and it will help me to AVOID the same problems.

Maybe if I get enough comments I can figure out which mobo to buy in order to replace this ASUS M4A78T-E.

Thanks in advance!

---

### Post by vtk on 2009-10-19
You and I have almost identical configurations, but I have 4 gigs of Corsair RAM and a slightly less meaty PS, a 550W from Seasonic.

I get the same thing, sporadic lockups, I mean *SOLID* no telnet, no nothing.
It could happen during install of an OS, it could happen browsing the web.  It frequently happens when formatting a drive.  I do have one thing I think I may have stumbled upon last night though.  I have 4 drives, 2 IDE and 2 SATA, and on installing Debian to see if it was something in Ubuntu breaking the system, the same thing happened, while formatting an IDE drive.

Just wondering if anyone else had any ideas...
V

---

### Post by HighlyDubious on 2009-10-19
> **vtk said:**
> You and I have almost identical configurations, but I have 4 gigs of Corsair RAM and a slightly less meaty PS, a 550W from Seasonic.

I get the same thing, sporadic lockups, I mean *SOLID* no telnet, no nothing.
It could happen during install of an OS, it could happen browsing the web.  It frequently happens when formatting a drive.  I do have one thing I think I may have stumbled upon last night though.  I have 4 drives, 2 IDE and 2 SATA, and on installing Debian to see if it was something in Ubuntu breaking the system, the same thing happened, while formatting an IDE drive.

Just wondering if anyone else had any ideas...
V

Thanks so much for taking the time to reply.

Yes, I've experienced the same problem. During the install it freezes solid. *NOTHING* works after the hang. And the fact that it's doing it from the Live-CD (which is supposed to pretty much work on any platform) is not a good thing. 

As mentioned above, my system is just 1 HD, (I've edited my OP to mention that it is SATA). And also a CD/DVD RW that's SATA. (no IDE devices). I've also added a 3rd party card-reader that is connected to one of the motherboard USB ports, but I don't think that's the problem.

One other thing. This weirdness happens no matter if I try to install from CD, or from a USB flash drive. 

Your experience with Debian freezing could be a strong clue that the problem is deep inside Debian itself. Since Ubuntu is based on Debian, and both Debian and Ubuntu are not working on this mobo for us, then it could be something about Debian.

As mentioned above, I have successfully installed PCLOS 2009.2 (x32) on this mobo, and although I've not tried to "stress test" it, I can say that after several hours of use, I didn't see any problems. PCLOS is based on Mandrake Linux, and so it may well be that whatever is different between Debian and Mandrake could give us a clue on this.

Unfortunately, I'm still mostly a newbie, so I'm totally over my head trying to figure out what the differences are between Mandrake and Debian that are causing our problems.

Regardless of all that. Thanks again for taking the time to post and tell your own experiences!

---

### Post by vtk on 2009-10-19
I'm going to try a few other things tonight, see what happens.  I am going to check all of the hardware connections again, set the BIOS back to default(in the process of trying to find out what was happening I changed some settings) and some other things.. I'll let you know what happens in the AM.
Peace,
V

---

### Post by neontrailer on 2009-10-19
Old AMD gamer here! I would pull out two sticks of that 1600 memory and then try it. That board should only handle 1600 MHz memory with a BIOS overclock on (one stick per channel) its just to much memory and its defaulting to 1333MHz with four slots full.......

---

### Post by cascade9 on 2009-10-20
I'd rip out more than just 2 sticks- 

[http://www.techpowerup.com/img/09-02-12/60a.jpg](http://www.techpowerup.com/img/09-02-12/60a.jpg)

Maybe this issue is fixed under windows and some linux distros but not under debian and deb based systems?

---

### Post by HighlyDubious on 2009-10-20
> **cascade9 said:**
> I'd rip out more than just 2 sticks- 

[http://www.techpowerup.com/img/09-02-12/60a.jpg](http://www.techpowerup.com/img/09-02-12/60a.jpg)

Maybe this issue is fixed under windows and some linux distros but not under debian and deb based systems?

WOW! I'm astonished at how resourceful people can be. I would have *NEVER* found that information! Wow!

Ok, my understanding of that link is that I have two choices:

[LIST=1]
[*]Rip out 1/2 my RAM (down to 4GB -- One stick per channel)
[*]Reduce the RAM speed down to 1066Mhz
[/LIST]
If I'm reading that correctly, either one of those should work.

As far as I'm concerned, the first is not even an option to me. I've made the switch to x64 on all my machines for all OS's (WinXP, Win7, Linux), and I did it so that I could access more than 3 1/2 GB's of RAM. I also paid $200 for a full 8gb of DDR3. And since this machine is used primarily under Windows, I'm not about to penalize Windows for the few times I run Linux.

So, I guess my only real option is to cut my memory speed by 1/3. It's certainly NOT what I want, but if it will work, then that's what I'll do. Fortunately, my mobo supports saving different BIOS settings "Profiles". Switching between them only takes a few extra keystrokes after a reboot. So maybe I'll make one BIOS settings profile for use with Windows (1600Mhz RAM), and one for Linux (1066Mhz).

Just one other random thought... It might be that if PCLOS was available in an x64 version, I might be experiencing the same problem. But since it's only x32, then I'm only accessing 1/2 my memory, and therefore (in effect), only accessing 1 DIMM per channel. 

In other words, if I spent a lot of time trying x64 distros, I might find the same problem with all of them. 

On the other hand, maybe if I were to stick with the x32 version of any distro (even perhaps Ubuntu and other Debian derivatives), then maybe the system will be perfectly stable. 

Hmmm... I'm almost curious enough about that to take the time to test the theory. (Or, at the very least, test Ubuntu x32) But for actual final set-up, I'll probably stick with the slower RAM setting, and not accept the reduction to 3.5GB.


Oh, wait... I just went back and re-read this whole thread. VTK has the same board, but only 4GB of RAM. He didn't say, but I'm guessing he's only using 2 sticks (2x2GB). He also didn't say if he's using x32 or x64, but again I'd make the guess that if he has the same CPU and mobo as me, then he's probably trying the x64 version. I notice he also didn't mention what speed his RAM is. In other words, there may still be some flakiness here that is in addition to the problem mentioned in the above link.

How about it VTK, wanna fill us in a bit more on your specs? Number of sticks? RAM speed? x32 or x64? Name of your 4th grade music teacher? (LoL)

---

### Post by HighlyDubious on 2009-10-20
> **neontrailer said:**
> Old AMD gamer here! I would pull out two sticks of that 1600 memory and then try it. That board should only handle 1600 MHz memory with a BIOS overclock on (one stick per channel) its just to much memory and its defaulting to 1333MHz with four slots full.......

Just wanted to thank you for taking the time to respond, and for bringing this limitation to my attention. It's already giving me some good ideas for things to google and try to find other people with similar problems -- and maybe other solutions as well!

Thanks  again!

---

### Post by cascade9 on 2009-10-21
> **HighlyDubious said:**
> WOW! I'm astonished at how resourceful people can be. I would have *NEVER* found that information! Wow!

Ok, my understanding of that link is that I have two choices:

[LIST=1]
[*]Rip out 1/2 my RAM (down to 4GB -- One stick per channel)
[*]Reduce the RAM speed down to 1066Mhz
[/LIST]
If I'm reading that correctly, either one of those should work.

As far as I'm concerned, the first is not even an option to me. I've made the switch to x64 on all my machines for all OS's (WinXP, Win7, Linux), and I did it so that I could access more than 3 1/2 GB's of RAM. I also paid $200 for a full 8gb of DDR3. And since this machine is used primarily under Windows, I'm not about to penalize Windows for the few times I run Linux.

So, I guess my only real option is to cut my memory speed by 1/3. It's certainly NOT what I want, but if it will work, then that's what I'll do. Fortunately, my mobo supports saving different BIOS settings "Profiles". Switching between them only takes a few extra keystrokes after a reboot. So maybe I'll make one BIOS settings profile for use with Windows (1600Mhz RAM), and one for Linux (1066Mhz). 

Heh, I found that image by luck, I wasnt looking for it. 

There is one other option- move your 2nd ram stick to slot 3, so you have 2x4GB but only in single channel mode. I'm not sure about single vs dual channel memory speeds with newer PCs, but in older machines it single channel  mode normally makes less than 10% difference compared to dual channel mode. 

BTW- 1600 Mhz? err..are you running an overclock?  

> **HighlyDubious said:**
> Just one other random thought... It might be that if PCLOS was available in an x64 version, I might be experiencing the same problem. But since it's only x32, then I'm only accessing 1/2 my memory, and therefore (in effect), only accessing 1 DIMM per channel. 

In other words, if I spent a lot of time trying x64 distros, I might find the same problem with all of them. 

On the other hand, maybe if I were to stick with the x32 version of any distro (even perhaps Ubuntu and other Debian derivatives), then maybe the system will be perfectly stable. 

Hmmm... I'm almost curious enough about that to take the time to test the theory. (Or, at the very least, test Ubuntu x32) But for actual final set-up, I'll probably stick with the slower RAM setting, and not accept the reduction to 3.5GB.

I doubt its 'only accessing 1/2 the memory so its only 1 dimm per channel'. It would still be accessing as dual channel, but only using 1/2 the ram chips on the stick. I would guess that whatever hack work around Ati/Asus has used is fine with windows and at least some linux distros, but debian based distros just dont deal with whatever they have done to the memory subsystem. Maybe a call procedure was dropped, and when the OS doesnt get a reply from the call, it makes the system unstable?  

It would be interesting to see if any of this hardware that goes flaky with debian/ubuntu works with another (64bit) distro.

---

### Post by HighlyDubious on 2009-10-21
Just a fast note.

After reading the above, I started doing some more research, and started to see more info about the potential speed problem. So I went into my BIOS with the intention to reset my speed back to 1333Mhz.

That's when I noticed that I've been lying. I *THOUGHT* I'd upgraded the BIOS when I built the system, but apparently I didn't. There it was, plain as day, telling me that I was using v2001 of the BIOS, when all along I thought I was using v2105.

So, I went ahead and upgraded from v2001 to v2105, and after doing so, I made sure the memory speed was set to 1333Mhz.

At which point, I booted into XP and Win7 just to double check they were still working (they were), and then tried again to install Ubuntu 9.04 (x64)

This time it went PERFECTLY!

Not one single glitch or weirdness. I've been running 9.04 for a few mins,  and done a full update of all packages. So far, it feels rock solid. Not even the smallest hint of instability. In addition, I've just now added Xunbuntu-Desktop with Synaptic, and still no hint of weirdness.

So, I'm sorry to admit that I've been lying all along. I *THOUGHT* I'd upgraded to the latest BIOS, but I had not. 

At this moment I don't know if the solution was upgrading the BIOS, or dropping back to 1333Mhz. But one way or the other, my system appears to be 100% stable and working great with Ubuntu 9.04 (x64)

Thanks for all the help and comments posted by everyone. And I truly hope this thread will be useful to the next person with the same problems on an ASUS M4A78T-E mobo.

:guitar:

---

### Post by vtk on 2009-10-22
Am running x64 for Ubuntu and Debian.
I have 4GB in 2X2 orientation
I've been trying a bunch of stuff (tenacious is my middle name), and have ruled out a few things.. 
Partitions can be on any disk, still locks.
It does not lock every time, just 9 out of 10 (I got past the partitioning once and had screwed up the Grub install so had to start over.. freeze city again *sigh*)
For me, it locks on creating the partition for / , no matter if it is on a SATA disk or on an IDE disk.
I've tried both ext4 and ext3, same result
Speed is full on 1600, will try and cut back as soon as I finish this... actually, I'll do it while I'm in here..
Well, I was a bad sysadmin, and changed two things at once.. I re-arranged the drives so the IDE would boot first AND shifted the RAM speed to 1066.
And it worked.  I cannot say for sure that it was one of these changes that worked, mainly because I'm not going to run the risk of continuing the amazing levels of frustration I'm experiencing with the first new (personally owned) system I've built in 5 years.  Once I complete the install I'll crank it back up and see if I get more sketchy behavior.
Peace,
V

---

### Post by cjlindem on 2009-10-22
I am posting because this is one of the threads I found on my path to fixing the freezing problem on my M4A78T-E last night.  Maybe my story can save someone else a lot of time.

I upgrade my system to an ASUS M4A78T-E, 3.2GHz quad core, 2x2GB DDR3 1600 ram about 3 weeks ago.  The upgrade went smooth but maybe once a day on average my system would completely freeze.  No error message, just solid lock.  It seemed more common while was using Virtualbox VM, but happened even just browsing the web or watching movies.  Happened in windows XP also (I dual boot).

Early on I had read that the board has trouble with ddr3 1600, and that I might need to find out the exact memory settings (latency, voltage, etc.) from the manufacturer and enter it into the BIOS.  I mostly ignored this, I've never had to do anything like that with ASUS boards before.  Never had to even obey their certified memory lists.  I'd just plug the ram in and things were fine and stable.  Not this time.  I found that the bios had assumed my memory was 1333.  I upped it to 1600, but lockups continued.  I upgraded to latest BIOS version, no difference.  I found WINE runs the popular burn-in software prime95, and tested it out.  With 4 threads running, one errored out with a division error in the first couple minutes.  Then another, then another.  Reading up on this said that it indicates a definite problem with either the processor or ram, and should never fail on a stable system.  I lowered ram's frequency back to 1333 in BIOS, and moved both chips into sockets next to eachother (into a dual channel config I think).  No good p95 still fails.  I was lucky to find my ram manufacturer's site (Mushkin) has a very helpful technical forum.  I found recommended manual settings to run the ram at 1600 and also settings for 1333.  The lead guy there said that AM3 is finicky about ddr3 1600, and that running at 1333 with lower cas latency will generally be almost as fast and cause much less trouble with the chipset.  I tried the settings for 1666 7-7-6-18.  Voltages between 1.85-1.9.  Still failed p95.  Finally gave up and changed it to the 1333 recommended settings.  6-6-6-18-1T @ 1.85V.  Prime95 ran for 12 hours without a single thread failing.  I have not gotten a lockup since.

In summary, if you have an ASUS M4A78T-E, your system instability may be caused by the BIOS's inability to correctly detect and configure the correct settings for your memory on auto.  Or the manual settings you've already entered for your ram aren't working.  I know this board is made for overclockers, but having to tinker with the memory settings so much just to get the system to run normally was really surprising to me, and disappointing.

---

### Post by HighlyDubious on 2009-10-22
> **cjlindem said:**
> I am posting because this is one of the threads I found on my path to fixing the freezing problem on my M4A78T-E last night.  Maybe my story can save someone else a lot of time.
  
.... Finally gave up and changed it to the 1333 recommended settings.  6-6-6-18-1T @ 1.85V.  Prime95 ran for 12 hours without a single thread failing.  I have not gotten a lockup since.

... I know this board is made for overclockers, but having to tinker with the memory settings so much just to get the system to run normally was really surprising to me, and disappointing.

Yes, I have to agree 100%. I am also disappointed. I thought I was buying a stable product from a company with a (generally) good reputation. But what I found was tons of frustration when trying to install Ubuntu 9.04 (x64) when my memory was set to 1600.

Very disappointing. Granted, there is not a humongous  performance difference between 1333 and 1600. But for me it's the whole principal of the thing. If a board maker advertises 1600, then I expect to be able to get 1600 and be stable across all platforms.

For now though, I'm running at 1333, and it appears to be stable. I'm disappointed and my experience leaves a bad taste in my mouth towards ASUS. Next time I am building a new system, I'll probably avoid ASUS and try another mobo maker. With so many other mfgs out there, there's no reason to remain loyal to a company that can't deliver on what they advertise. If I'm going to spend my hard earned money, I'll do it with a company that delivers what they promise.

For now though, bottom line is, yes, if you're using a M4A78T-E, then don't even bother buying 1600 memory. Just save yourself some money and get the 1333. Trust us, it will save you many headaches in the long run.

---

### Post by HighlyDubious on 2009-10-22
> **vtk said:**
> Am running x64 for Ubuntu and Debian.
I have 4GB in 2X2 orientation

Thanks for filling us in on your configuration. It tells me that the problem doesn't just occur when all 4 slots are full.

> **vtk said:**
> Well, I was a bad sysadmin, and changed two things at once.. I re-arranged the drives so the IDE would boot first AND shifted the RAM speed to 1066.
And it worked.  I cannot say for sure that it was one of these changes that worked

> **vtk said:**
> Once I complete the install I'll crank it back up and see if I get more sketchy behavior.
Peace,
V

Yes, I did pretty much the same thing, but in reverse. After getting Ubuntu up, running, and stable at 1333Mhz, I rebooted and changed a few different things in the BIOS. At the same time I also bumped my speed back up to 1600Mhz. Next time I rebooted, Ubuntu froze on me within 5 mins. At which point I mentally kicked myself for changing several things at once.

On the other hand, I then went back to BIOS, and this time changed only *one* thing. I reduced the speed back to 1333Mhz, and next time I started Ubuntu it worked perfectly for several hours. So, I'm pretty sure that the whole problem all along has been trying to use the 1600Mhz that we were (mis)lead to believe our mobo could handle.

---

### Post by HighlyDubious on 2009-10-22
I'm marking this thread as "Solved" because it seems that updating the BIOS (current latest version is v2105), and reducing the memory speed from 1600Mhz down to 1333Mhz has fixed things. 

It's not a solution I'm happy with, but it is a functional solution, so for now that will have to be "good enough".

If anyone else has more to contribute on this topic, I welcome any other comments. Who knows, maybe somewhere out in the big wide world, there's a mad hacker with the perfect working solution to allow us to use our 1600Mhz memory at it's rated speed! :wink:

---

### Post by cascade9 on 2009-10-23
> **HighlyDubious said:**
> Yes, I have to agree 100%. I am also disappointed. I thought I was buying a stable product from a company with a (generally) good reputation. But what I found was tons of frustration when trying to install Ubuntu 9.04 (x64) when my memory was set to 1600.

Very disappointing. Granted, there is not a humongous performance difference between 1333 and 1600. But for me it's the whole principal of the thing. If a board maker advertises 1600, then I expect to be able to get 1600 and be stable across all platforms.

For now though, I'm running at 1333, and it appears to be stable. I'm disappointed and my experience leaves a bad taste in my mouth towards ASUS. Next time I am building a new system, I'll probably avoid ASUS and try another mobo maker. With so many other mfgs out there, there's no reason to remain loyal to a company that can't deliver on what they advertise. If I'm going to spend my hard earned money, I'll do it with a company that delivers what they promise.

For now though, bottom line is, yes, if you're using a M4A78T-E, then don't even bother buying 1600 memory. Just save yourself some money and get the 1333. Trust us, it will save you many headaches in the long run.

I wouldnt be at all suprised if there was improvements from getting the newer BIOS. Even if you still dont get stable performance at 1600 Mhz, its possible that things still would have been  unstable at 1333 Mhz with the old BIOS. Bit hard to tell though (and I would never even think about going back to the old version, just to test LOL)

To be honest, I'm not a huge fan of Asus these days. But in the defence of them, here what the specification page for the M4A78T-E says-
Asus-
> 4 x DIMM, Max.  16  GB,  DDR3  1600(O.C.)/1333/1066 ECC,Non-ECC,Un-buffered MemoryThey dont exactly make is clear that 1600 is overclock only. But the other guys do the same- 
DFI (BI 785G-M35)- 
> Supports DDR3 1600(O.C.)/1333/1066/800 MHzMSI (790GX-G65)-
> DDR3 800/1066/1333/1600(OC)Gigabyte is even nastier. Mind you, I didnt check the RSS feed for specifications, it might make it slightly more clear there. Or it might not.  (GA-MA790GPT-UD3H)-
> Dual Channel DDR3 1666+ for remarkable system performance  At least foxconn doesnt say '1600 OC', but they dont even support 1600 Mhz- Foxconn A7DA-S 3.0- 
> Dual channel DDR3 1333/1066/800 x 4 DIMMs, Max. 8GB  Its just a pity that they dont make things clearer in the pages, but its probably a bit of the old 'keeping up with the Joanses' problem. Once someone has started saying '1600' everyone else wants to follow.

> **cjlindem said:**
> I know this board is made for overclockers, but having to tinker with the memory settings so much just to get the system to run normally was really surprising to me, and disappointing.

Well...no offence, but I wouldnt call any 790GX chipset for overclockers. It able to overclock, yes, but if you want to overclcock, get a 790FX if you have the money, or a 770 otherwise. Chipsets with intergrated video are always more of a pain than those without.  

I wonder if the actual memory modules are part of the problem? I do know that some chipsets are picky about the memory used. Asus doesn't appear to have a memory support list for that baord, the gigabyte one lists corsair modules, but  HighlyDubious is running CMX4-XXXX and the page says CMX3-XXXX. It would be interesting to see if one of the rated modules will actually run stable at 1600. [FONT=Tahoma][SIZE=2]
[/SIZE][/FONT]

---

### Post by Language on 2010-02-18
I had a similar problem. Using the M4A78T-E, with bios v2105, 1TB hdd, 4GB DDR3 1333mhz, I experienced the following behavior:

9.10 installer hanging (using ext4) at "5%" and a null pointer kernel exception followed by a lockup. Tried multiple times, always failed at same spot. 

9.04 installer worked after running gparted seperately(ext4), upgraded to 9.10, had to manually run FSCK after reboot. Ran all updates, had to fsck again after that.

Tried reinstalling 9.04 with ext3 after reading about ext4 issues, install crashed at around 80%. Reinstalled again, install succeeded, but could not boot after reboot.

Finally looked for an up to date bios after reading this thread. Installed latest bios (v2503). Did a fresh install of 9.10 (still using ext3) and everything worked perfectly. No hangs, no errors, no running fsck after reboot.

Success! :D


Are any of you running ext4? I'm a little gun shy about it on this setup after reading horror stories and having my own bad experiences, but I'm wondering if it was ext4's fault or the bios.

---

### Post by kubu88 on 2010-02-18
Hi!Do you think it happen only with DDR3? I'm experiencing the same kind of freeze with M3N78-vm. 2gb ram kingston 800mhz on board

---

### Post by HighlyDubious on 2010-02-20
> **Language said:**
> I had a similar problem. Using the M4A78T-E, with bios v2105, 1TB hdd, 4GB DDR3 1333mhz...

Finally looked for an up to date bios after reading this thread. Installed latest bios (v2503). Did a fresh install of 9.10 (still using ext3) and everything worked perfectly. No hangs, no errors, no running fsck after reboot.

Success! :D

Are any of you running ext4? I'm a little gun shy about it on this setup  after reading horror stories and having my own bad experiences, but I'm  wondering if it was ext4's fault or the bios.     

I'm afraid I can't contribute a whole lot more at this point. My M4A78T-E system has been "on loan" to someone for about 3 months now. In fact, I only had it up and working for about 2 weeks before loaning it out. At this point the "loan" is starting to look more like a semi-permanent situation, and so it could be several months before I get it back. 

As far as ext4, at the time I was trying to get that mobo working, 9.10 was still in beta, and 9.04 did not natively support ext4 from the Live-CD. I think I tried 9.10 beta (with ext4) back then, but I'm sure that I if I tried that, it would have been under the v2001 bios, and 1600Mhz. Which means it would not have worked due to the above listed problems.

Since it could still be several more months before I get my M4A78T-E machine back, I'm asking this more out of pure curiosity than an actual need to know. You mention that you upgraded to the v2503 bios and the system became stable, so I'm just curious, are you still using 1333Mhz, or did you crank it up to 1600Mhz?

Either way, it is nice to see that ASUS seems to be making a sincere effort to improve the stability of this mobo. A quick check of Asus website shows that in the past 5 months they've brought out 5 bios updates. Some could argue that shows the mobo has numerous problems if it needs so many updates. On the other hand, it also suggests that Asus is making a sincere effort to address these problems. This seems to be especially the case with the v2503 release, which they describe as "Improve system stability". So, perhaps when/if I get my M4A78T-E back, I might be happy to discover it finally works at 1600Mhz, as advertised. :)

Either way, thanks for posting to this thread. I'm sure your info will help someone else out there who's having problems with this pesky board. ;)

---

### Post by HighlyDubious on 2010-02-20
> **kubu88 said:**
> Hi!Do you think it happen only with DDR3? I'm experiencing the same kind of freeze with M3N78-vm. 2gb ram kingston 800mhz on board

Wow, I couldn't even begin to guess. You might try searching the forums for any mention of your mobo. And if nothing useful shows up, then try posting your problem and question in a new thread. That's what I did with my problems on the M4A78T-E, and as you can see, the responses I got really helped. 

Best of luck to you. ;)

---

### Post by molejo on 2012-11-18
Hello everyone,

I've got similar problems, but I use 1333 memory...
for a very long time I used it with most of automatic RAM settings except clock speed on memory 1333 and 1600 on next two bios options (don't really remember now which clocks exacly)

I upgraded bios almost every new update, but still had issues mostly under linux Ubuntu (from 9 to current 12).
The issue was freezes while file copy - when more than about 5 gigs to be copied it froze.

Under windows (7) sometimes I got freezes but veeery rarely.

I dropped now memory to 1066 leaving rest on auto - and it runs perfectly... no freezes at all even with prime95 (on wine) which used to hang on other settings as well as copying files...

I'll try to get some faster and more memory for testing, and I'll hopefully find good solution for this :)

greetz

---

### Post by molejo on 2012-11-18
I've just played a little bit with settings
and resulsts are quite nice... but i'm not yet sure it's good and stable solution.

I;ve got 2 x 2GB 1333 CL9 powered 1,5V by manufacturer and working in dual channel.

I've set 1333 dram clock and 1,6V dram voltage (raised by 0,2 each time prime hanged after few seconds) rest is auto.

right now Prime is finishing his mixed tests and everything seems ok - "rock solid stable" - I hope ;P

so I guess solution is applying certain clock and voltage - for your memory, which might be higher than theoreticaly should be...

Hope that will help ;)

---

### Post by wildmanne39 on 2012-11-18
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


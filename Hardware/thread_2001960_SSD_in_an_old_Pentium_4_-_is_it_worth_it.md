---
title: "SSD in an old Pentium 4 - is it worth it?"
date: 2012-06-11
forum: Hardware
---

### Post by bigwoof on 2012-06-11
Hi there,

I have been looking to improve the boot time of an old P4 machine at home (it is my mythtv backend so I want it to boot quickly when it gets the WOL from the frontend).

I have heard that an SSD can improve the boot time of most computers however I am not sure if my old machine can benefit. It has an intel D865PERL mobo which supports SATA1.

From my research it looks like the machine will be able to work with a new SATA3 SSD but I am wondering if it will make any difference to the machine. 

Here are my thoughts:
- Read/write speeds 1.5 Gbit/s - is the max my mobo can do (even though the drive may be capable of more). I am not sure if this is that important for my aim - as it may be more important for working with large files where the sustained read write speed is more important - probably not to important for booting.

- seek time - I think that this is where the SSD may make the most difference as this is almost instantaneous (0.1ms) - my understanding is that during boot the machine is accessing all parts of the drive and seek times are important for a fast boot. 

If I am correct then it will be worth me buying the new SSD for this old machine.

What are your thoughts?

Cheers

Phil

---

### Post by ahallubuntu on 2012-06-11
Is there some reason you can't put the system into Standby (Sleep) so it never really shuts down?  Resume it and it is up and running pretty quickly.  I do this for both of my media center boxes.

An SSD would certainly improve the boot time, but it still wouldn't be instantaneous especially on an old machine.  Just the POST may take 2-3 seconds (there's no POST if you resume from standby FYI).  It's up to you if you feel the need to invest in an SSD just for that purpose.  But if you are - why not invest a little more in newer hardware?

---

### Post by papibe on 2012-06-11
Hi bigwoof.

Sure it will be faster, but since they are kind of expensive I don't know if it will have a good investment/benefit ratio.

For instance, I'm very impress by what a simple Compact Flash Card can accomplish. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1904013&highlight=life+laptop") with some benchmarks.

Just some thoughts, if it is within your budget, go for it ):P
Regards.

---

### Post by bigwoof on 2012-06-11
Thanks ahallubuntu,

> **ahallubuntu said:**
> Is there some reason you can't put the system into Standby (Sleep) so it never really shuts down?  Resume it and it is up and running pretty quickly.  I do this for both of my media center boxes.

I had endless troubles with getting this machine to sleep when I first set it up so I just went with letting it power itself down and booting when it needs to.  This also got the tick of approval from my wife (to save on the power bill).  

> **ahallubuntu said:**
> 
An SSD would certainly improve the boot time, but it still wouldn't be instantaneous especially on an old machine.  Just the POST may take 2-3 seconds (there's no POST if you resume from standby FYI).  It's up to you if you feel the need to invest in an SSD just for that purpose.  

It doesn't need to be instantaneous - just quicker than the frontend :)

> **ahallubuntu said:**
> But if you are - why not invest a little more in newer hardware?

I would love to upgrade the hardware however as PhD student I do not have the budget at the moment. $60 for a 60GB SSD seams reasonable to me. The other reason to buy a new drive is to upgrade to 12.04 LTS without messing with the current install on the old drive.

---

### Post by bigwoof on 2012-06-11
Thnaks papibe,

> **papibe said:**
> Hi bigwoof.

Sure it will be faster, but since they are kind of expensive I don't know if it will have a good investment/benefit ratio.

For instance, I'm very impress by what a simple Compact Flash Card can accomplish. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1904013&highlight=life+laptop") with some benchmarks.

Just some thoughts, if it is within your budget, go for it ):P
Regards.

The thread looks interesting.  I will look into it but I reckon that $60 for a 60GB SSD is reasonable enough, since prices have dropped lately.

---

### Post by ahallubuntu on 2012-06-11
Yes, I have a couple of old Pentium 4 systems, and I have had issues with Suspend with them as well.  Really depends on the chipset and the motherboard.  You might try the newer versions of Ubuntu, however - maybe the newer kernels do better with the older hardware?

Personally, I would invest that $60 in a newer motherboard/CPU and not in an SSD.  You might look for a Core 2 Duo system (or a Pentium Dual Core or even a Celeron Dual - but not "Celeron D" or "Pentium D"!).  I've had great luck with suspend in Ubuntu in this newer technology.  I have one Ubuntu server with a Celeron Dual Core (Core 2 Duo with less cache) that I routinely wake up from suspend with Wake On Lan - it's extremely reliable.  

Other benefits of a Core 2-based computer: lower power consumption for one.  The Pentium 4 was a heater.  Intel's Core CPU architecture was a major shift for them - they dumped the Pentium 4 architecture entirely because it was lousy for power consumption.  A Core 2 Duo running at say 2GHZ is actually faster (even with just one core) than a 3GHZ Pentium 4, because the architecture is much more efficient.  But with two cores, it would be even faster!  And use about half the power, give or take.  I've put them on watt meters - it's true.  Cooler means less heat too and a quieter CPU fan.

And a newer motherboard means probably 3.0Gbs SATA for future use.

P4 is just old technology and not Intel's finest hour.  Of course, you COULD buy an SSD now and use it later on some newer system.

FYI, where I live I can sometimes find pretty cheap Core 2-based towers.  Core 2 Duo is old now too - replaced by i3/i5/i7.  But Core 2 is really great stuff, yet you might find some deals.  I bought a Dell 1.6GHZ Pentium Dual Core tower recently for $80 USD.  (Pentium D FYI is *NOT* the same thing - Pentium D is really two P4 chips in one and REALLY hot!  "Pentium Dual" despite the similar name is something newer, better, and cooler!)

Anyway, I've diverged from your original question - just some things to think about.

---

### Post by BeenLikeFlynn on 2012-06-11
dear god no.

---

### Post by bigwoof on 2012-06-12
ahallubuntu,

You bring up a good point - I will probably upgrade the old P4 or a better system in the future - in the mean time I will probably get the SSD - and use it in when I get round to upgrading the P4. 

Thanks for the info

---


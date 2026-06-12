---
title: "Experienced System Builders... some advice?"
date: 2008-11-17
forum: Hardware
---

### Post by decoherence on 2008-11-17
I've posted this on "via arena" forum as well but thought I might get a quick response here, too.

I have a Via CN 10000 embedded motherboard. The problem is the video. Sometimes it doesn't work at all, sometimes it's fine, sometimes it will glitch out and freeze the system. It sometimes does this during POST so I know it's not an issue with linux drivers. This is with the on-board UniChrome graphics or whatever it's called.

I have swapped out LCD panels and cables, neither of which seem to have an impact on the random nature of this.

So my question to system builders more experienced than I (not hard) is; if you had intermittant video, and you had ruled out the cable and the panel as the culprit, what would be your next suspicion? What things would you try before chalking it up to bad hardware? And have you ever seen bad hardware behave in this way?

I'm trying to dig up a PCI graphics card for testing... though it won't fit in the case I'm using so not really a solution.

Any and all insights very welcome!

---

### Post by phidia on 2008-11-17
You don't say what operating systems you have tried on this.

I would definitely not base anything on one distro and with 8.04 & 8.10 adapting different xorg methods (methods that are not complete-it seems) you could definitely experience some problems using either of those.

Try using antiX, mepis or sabayon, before you conclude this is a hardware issue.

Added: It would help if you said if the symptoms you described are random or connected to any processes.

---

### Post by mrtomservo on 2008-11-17
I have personally experienced bad onboard components before.  Once it was onboard video.  XP, Linux, all had problems.  Random freezes, bios beeps indicating a hardware problem.  Ended up disabling the onboard video and added a cheapo video card.  

Perhaps you could check and see if you need a bios update?

---

### Post by decoherence on 2008-11-17
> **phidia said:**
> You don't say what operating systems you have tried on this.

It will freeze before any OS is loaded. In fact, if it gets far enough to start X, it seems to be solid (that's Xubuntu 8.10, btw.) I wouldn't put too much stock in that though. Since it rarely even gets to GRUB, I can't really say for sure that it IS solid or if it was just a co-incidence.

So, just to be very clear, when I say "often it doesn't work at all" I mean "I power up the motherboard but the panel still reports 'no signal'" -- but sometimes it does, and starts to POST, glitches and then dies with a video freeze. Or sometimes I get to X at which point all appears to be OK until I turn my back on the thing and THEN it dies (of course!)

Anyway, pretty sure it's not OS specific.

---

### Post by phidia on 2008-11-17
Given all that. I would recheck all connections and reseat the memory. 
If it's random as you've described it could be a poor power connection (on board) or a faulty PS.

---

### Post by decoherence on 2008-11-17
> **mrtomservo said:**
> Perhaps you could check and see if you need a bios update?

That's a good call. Unfortunately to check that I need to get in to the setup screen and the thing is being a real punk right now.

On top of that, I can't find a non-Windows version of their BIOS updater... anyone? Guess I'll just install Windows on another computer, swap the hard drive and see if it will get far enough for me to run the updater...

That's a bummer for a company that maintains its own "linux portal."

---

### Post by decoherence on 2008-11-17
> **phidia said:**
> Given all that. I would recheck all connections and reseat the memory. 
If it's random as you've described it could be a poor power connection (on board) or a faulty PS.

Ah... the power supply is a PicoPSU which is basically a DC/AD converter in ATX power form factor that connects to a laptop style power "brick." I've heard of some people having strange issues with them (though not a lot of answers!) so I'll try plugging a regular power supply and see if I have better luck.

Thanks for the pointer!

The only other thing I have not swapped out is the PATA hard disk. Anyone ever hear of that causing this sort of issue?

thanks again, all

---

### Post by cariboo on 2008-11-17
IF you can find a can of coldspray, give the video section of the board a good shot to see if that makes a difference, If it starts up while the chip is cold, then you probably have a failing video  chip.

Jim

---

### Post by decoherence on 2008-11-18
Well I went home for the night and cannibalized an old system for a PCI rage 128 card. I plopped it in a few minutes ago and the system booted without so much as a hiccup. Sadly, the card is way too big to fit in the this particular case.

I'll apply the BIOS update and continue to test for a video freeze but it's looking a lot like bad video hardware to me. Royal bummer.

EDIT: Just has another hard freeze, this time in full X11. Swapping the RAM module and trying again...
EDIT2: Yep, now it's behaving just like it was before, even with the PCI graphics card. I started pinging it with another computer and went off to do something else. When I got back, it was still successfully responding to pings, but when I switched my KVM to it, the GUI froze and the pinging stopped working.

Sooo.... a USB related issue?? Or perhaps it really doesn't like my KVM? Gotta try a proper PSU as well.

tsk, such a pain...

EDIT3: Using a regular PSU now... so far so good.

---

### Post by mrtomservo on 2008-11-18
Sounds like you're narrowing it down pretty well, excellent!  If the PSU doesn't seem to solve the problem, maybe you could try isolating the mother board from the case.  Perhaps it's grounding out to the chassis.

---

### Post by decoherence on 2008-11-19
> **mrtomservo said:**
> Perhaps it's grounding out to the chassis.

Heh, while going through all of this I've been thinking that very thing to myself and praying it's not the case, because as best I can tell, it shouldn't be grounding out on anything, but it's a VERY custom case and of course I can't see the internals when it's closed...

But it has been running fine all night with the 'real' PSU so I'm optimistic. Thanks for your help everyone!

---


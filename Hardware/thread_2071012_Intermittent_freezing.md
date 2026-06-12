---
title: "Intermittent freezing"
date: 2012-10-14
forum: Hardware
---

### Post by colvirk on 2012-10-14
Good morning all,

I have been trying to diagnose an issue with my computer over the past few weeks and I have not had any luck. My issue started in windows 7. The computer booted into windows fine but after opening a any file or folder the HDD activity light would come on and the computer would freeze. The mouse would move but the keyboard would not respond. After one minute everything would "unlock" and I could use the system again. This happened every boot once then would happen intermittently. 

I wiped the drive and installed the most current version of Ubuntu thinking it was a software issue. The issue continues after a second install of Ubuntu. Once logging in, if I try to access the main 250GB drive, the 1TB storage drive, or a 16gb thumb drive the computer freezes for a minute and then unlocks. I can watch a 2.5 hour video after that. I ran the WD diagnostic tools on the hard drives and MEMTEST on the RAM with no errors.

I am now at a loss where to go. This machine is where I am trying to keep all my videos and pictures of my new born along with editing them. Needless to say my wife is pressing me hard to get this fixed! Thanks in advance for any suggestions you  all have!!!

---

### Post by ahallubuntu on 2012-10-14
First and foremost: it's important to make sure all those pictures of your new baby are BACKED UP somewhere.  Are they?  My golden rule is to have at least two copies of every file I care about, on different devices.  Hard drives fail all the time sometimes without warning, and you could lose everything.

Have some sort of backup scheme in place - either a second hard drive or backing everything up online.  Something.  Just to make sure...

Failing hard drives can cause symptoms like you describe, but it sounds like you have ruled that out in your case.

The next step is to rule out other causes.  If you ran Memtest for a while and the RAM is OK, the next things I would look are are: failing power supply and overheating CPU.

I assume this is a desktop computer.  Then it probably has a standard power supply.  You could test that power supply or swap in a replacement.  Sometimes power supplies start to fail or can no longer supply quite enough power for what you have in your system (say, after adding some hardware).  Also, power supplies are one of the most unreliable pieces of a PC (along with hard drives).  It is very common for them to fail, sometimes obviously (no power at all), sometimes not.

The CPU in your computer must also be kept cool.  There is a heat sink on top of it to draw off heat and a fan to blow over the heat sink to keep it cool.  If the heat sink gets clogged with dust or the fan stops working (or gets dirty), the CPU can overheat and cause glitches like you describe.  You can examine it for dirt/dust or just clean it out if it's dirty.  Make sure the CPU fan is working.

If you have other cards - video cards, add-on cards - try removing everything possible not to use and run without it.  If you have a discrete video card, it could also be the culprit (and may also have a fan - if so, make sure it's spinning).

Beyond that, if you have tested everything else and ruled it out, some component of the motherboard could be failing.  In that case, it's usually not practical to repair it - you just replace the motherboard or get a new computer.  Sometimes you can see capacitors bulging on the motherboard - that's a sign of likely failure.

---

### Post by colvirk on 2012-10-14
Thanks for the advice on backing up. We have everything on the 1 TB drive as the backup and most everything edited is uploaded to picasa. 

I did some more research and I think that the issue is RAM. This is a desktop PC and for some reason I am running I bought DDR2 800 for my machine and the motherboard manual says that it is supposed to use DDR2 667. Even more interesting is the box says it's compatible with 800.

I built this machine in 2006 and really have had no issues with it since. The issues started long after I added 2 hardware components: a second 2GB kit of RAM and a new PCI-Express video card with HDMI. The voltage looks a little high on the RAM in the BIOS (1.9V where the corsair website says it should be 1.8V). I removed both kits and swapped them in the paired slots (keeping them in the original kit configuration but swapping them in the slots of the MB) and this seems to have fixed it in the short term today.

---

### Post by ahallubuntu on 2012-10-14
You realize that adding a PCI-E video card adds load to the power supply, right?  It could well be your power supply can't quite supply the peak load required for that card.

If Memtest shows no errors with your RAM, it's almost certainly not the RAM.  I've run DDR2 800MHZ RAM in motherboards that are spec'ed for slower RAM several times without issue.  I have also installed incompatible RAM that would sort of work but Memtest would show immediate errors.  If in doubt, run Memteset overnight in a loop.  If no errors in the morning, it's certainly not the RAM.

You could use this time as an excuse to buy a more efficient power supply.  Almost certainly that 2006-era power supply isn't 80+ rated and uses more power than a new 80+ power supply would.  I regularly see 430watt and higher 80+ power supplies on sale for $20 USD after rebate.  If that's a higher rating than your existing PSU, it might solve your problem and wind up saving you money (eventually) anyway as it would use less power than the existing one.

---


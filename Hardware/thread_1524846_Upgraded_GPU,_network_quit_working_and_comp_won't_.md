---
title: "Upgraded GPU, network quit working and comp won't restart"
date: 2010-07-05
forum: Hardware
---

### Post by Elokin6 on 2010-07-05
Hi all.  Hope this is the correct subforum for this post.

I just bought a new PC yesterday.  The first thing I did was swap out the power supply (the bugger only came with a 250w) and install my GeForce 9400 GT.  I installed Lucid and everything seemed great, but now I'm experiencing some weirdness.  First, my wired network quit working after a reboot.  Then, when I went to reboot my computer to see if it that would fix the problem, the damn thing wouldn't reboot.  It just went into the login screen when I clicked restart or shutdown.  I had to use sudo halt to get it to shut down.

I took out the graphics card and am running with the onboard one. Everything seems to be working at the moment.  My first thought was that my power wasn't sufficient to run my GPU, but this doesn't make a lot of sense.  The current power supply is a 300w (min recommended for this card) and the 9400 GT is supposed to pull 50w max.

What do you guys think?  Maybe the power supply is heading south?  Maybe the issues are totally unrelated?  Has anyone else ever experienced anything like this this?

Thanks in advance for your help.

---

### Post by djinnkeeper on 2010-07-05
GPU power requirements are notoriously underrated.. Also, to make matters worse, PSUs tend to have the opposite problem .. (they'll get away with listing their peak wattage, when the average is actually about 100w less..)

When you're buying a power supply for a particular prerequisite (like a GPU or a buttload of memory and drives) it's important to either over-do it by at least 150-200w.. or make sure that the PSU is advertised as "continuous" power, so you won't have to look at averages and peaks.

If your card requires additional power, make sure it's plugged in.  Also, check the 12v rails to make sure their amperage meets (or exceeds, hopefully) the requirements of the GPU.

I'm running a 9600gt with 512mb of DDR3.. my PSU is a 650w Antec Earthwatts, upgraded from a 550w Gigabyte Superb (dunno if I'd call it "superb" ..they should've called it the *Gigabyte Okay*)  Part of my power suckage problem is probably DDR2 ram (8gb of it)

---

### Post by Elokin6 on 2010-07-05
Thanks for the info. :)

So this does sound like a power issue to you?  Guess I better save my pennies and pick up a better power supply.

Thanks again

---


---
title: "ubuntu live cd killed my laptop?"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by dchosen on 2009-03-31
Hello, I have a problem hopefully someone can help me solve. I booted into the latest stable version of ubuntu desktop. I am mainly a windows user, but am slowly embracing linux. I was running f-prot from the live cd, just to see what kind of results I'd get. During the middle of me using the live cd, the computer suddenly shuts off.  I thought no big deal, I'll just boot up ubuntu again and start over.  I get to the boot menu where I can select to launch it into live cd mode. It get to the loading image and stays their for a while, then pops the cd out and the computer turns off. I then said oh well, and left the disk out as I would just log back into windows xp and be on my merry way.  I get to the windows loading screen and then the screen goes black and the computer shuts off once again.

I tried a variety of solutions. I first attempted to get back into ubuntu, I can do this by disabling acpi, this is odd considering all of the other times I've used ubuntu cd I never had to do that. But, I can mount the hardrive, browse internet and everything when its loaded this way.  I do a proper shutdown, which when I hit enter at the end it never really actually shuts off.  I decided, that my mbre may be damaged.  good thing I have 2 original xp disc, one for pro and one for home.  I stuck the pro disc inside first even though I have home installed on the pc. For the recovery console this doesn't matter right? well as soon as i press (r) to go to the console, the power shuts off.  I thought, that maybe it was the mismatch of editions. So I threw the home edition cd in and it did the same thing! Ok, so now im ready to just nuke the machine, so instead of pressing (r) on the giant blue and grey screen I will just hit enter to reinstall windows, but guess what? it shuts off in the same matter. so how could I reinstall now?

Has ubuntu killed my laptop because of this unclean shutdown? I have ran the memory test, its fine.  I have tried various boot cds to no success.  Has anyone had this problem, and how did you fix it.

Specs:
80 gb samsung hd
2.2 intel core
2 gb ram ddr2 

(TO RECAP: I can boot into unbuntu and do things for hours by disabling acpi in the options, However, this is not what I want, I want windows and ubuntu to load like it did before the above happened)
Thank you for your time

---

### Post by cariboo on 2009-03-31
Have you considered that it may be a hardware problem, maybe overheating that causes the shut sown?

Jim

---

### Post by spcwingo on 2009-03-31
I second that idea.  Definitely sounds like an overheating, or other hardware problem.

---

### Post by Mark Phelps on 2009-03-31
You mentioned ... laptop.

I have an old HP laptop that suffers from the problem that the internal CD drive gets very hot after a while -- so hot that the laser is unable to read the CD anymore.  So, to install anything or copy from CD, I have to do that right after cold booting the machine.  That could account for read failures if you're trying to use a CD after the machine has been on for a long time.

As to just shutting down -- I agree that sounds like a heat problem. Laptops typically have fans that automatically start up after the temps reach a certain level.  If your laptop fan and/or thermal sensor have failed, the fan won't be able to keep the machine cool enough and it will shutdown automatically.

Either way, it's a hardware failure.

---


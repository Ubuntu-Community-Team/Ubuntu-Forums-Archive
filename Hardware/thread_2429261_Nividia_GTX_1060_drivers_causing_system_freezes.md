---
title: "Nividia GTX 1060 drivers causing system freezes"
date: 2019-10-16
forum: Hardware
---

### Post by MZ250Supa5 on 2019-10-16
Is anyone else experiencing system freezes? Well, maybe it's just x11 freezing, but effectively the only way to recover is a hard reboot. I've been having this issue ever since I bought this video card over two years ago, Initially it was installed on my prior system, based on this hardware:

MD FX-8120 8 Core 3.10GHz - Gigabyte GA-78LMT-USB3 HDMI Motherboard - 32GB DDR3 RAM

Initially when I got this hardware I used a GeForce GTS 450, which worked fine, if somewhat loudly on full throttle, which I then changed for a passively cooled GT 640. again with no issues. However, as soon as I installed the GTX 1060 I started to experience serious freezing up issues, usually when viewing graphically demanding things such as Second Life/OpenSimulator using full Advanced Lighting. 

Last year I decided to change the hardware of my computer once again, opting to go for a basic gaming setup, using a motherboard that required a discrete gpu as it had no graphics chip to cause potential conflict. This system is basically this:

 AMD Ryzen 3 1300X Quad Core 3.7GHz CPU, ASUS Prime A320M-K Motherboard Bundle  8GB DDR4 2400MHz RAM

Both systems obviously have plenty of RAM and are well up to the job of running this graphics card, but still the system randomly froze. I have no such bad behaviour when using this video card on Windows 10 and  the system works flawlessly, but no matter what Linux distro I use, (thus far tried on Ubuntu MATE, and also Manjaro MATE - similar results, and soon freezing up at the slightest glitch, and also what I'm using now, Xubuntu, which I pretty much hate, but initially at least it didn't freeze so much, but now I'm experiencing several freezes a day, and this is not doing my temper any good.

I strongly suspect that Nvidia are to blame for this. and when I contacted them last year over the issue, they acknowledged that there have been issues of this nature, however the solution they suggested was outdated and a complete waste of time - basically I'd been brushed off. I wouldn't mind so much, but it's not as if the GTX 1060 was a cheap as chips graphics card. It's not the most expensive, for sure. but it's not something you'd buy merely for connecting a computer to your TV set either. Plus. I need something that will support 3 monitors out of the box - two Hanns G HS243 and a Parblo Coast 22 pen monitor, (monitor with graphics tablet functionality built in, which isn't officially supported to run on Linux, but there are ways). 

After 10 years plus of using Linux of one form or another I don't want to have to be forced back to using Windows again, just switching on the system reminds me of why I abandoned Windows in the first place, not the least of which is the completely insane and inconsiderate update system. I still have Windows as I do still use it, partially for testing things that I do, but also to run programs that will not run on Linux any longer, or at all. 

I really do hope someone out there has a solution. My other suspicion is that the old issue of the nouveau drivers conflicting with the nvidia is the culprit, as it's not possible to completely remove the nouveau, only disable the buggers, which, if my memory servers me right, was causing issues when proprietary drivers were installed about 10 years ago. 

But i guess it's really just a case  of, as Linus Torvalds exclaimed "f****ing Nvidia!"

---

### Post by Autodave on 2019-10-16
What driver are you using and where did you get the driver from?

---

### Post by MZ250Supa5 on 2019-10-16
I'm using the 430 driver that I got from the graphics-drivers ppa, but this issue has been present since 396 at least. One thing I have noticed though is that when I do a fresh install for a while, though still prone to freezing the problem becomes progressively worse the longer any particular os has been running. This has nothing to to with the system not being rebooted, as the system has to be rebooted in order to recover - personally I would rarely ever actually ever need to reboot as I run the system 24/7 - it provides useful background heat in my living room!

Once in the past I had issues with the drivers provided by the community, and contacted Nvidia through live chat and communicated with a really helpful agent who advised me to use one of their bleeding edge drivers, which of course had to be manually installed, but as I've done this many times previously, (I don't like doing this as sometimes kernel updates are so frequent that re-installing the various add-ons I use becomes a chore) I'm comfortable doing this. This is my next step, failing anything else other people suggest might be the case.

---

### Post by Autodave on 2019-10-16
I know that many people here run that particular card with no issues.  To my way of thinking, since you have had that issue with that card on 2 different systems, I would be thinking that the card itself is the problem: defective, overheating, etc.

Have you had Windows running a long enough time period to know that it doesn't happen in Windows?

I run nothing but Nvidia in all of my machines: from a 1/2 gig cheapy one up to my RTX 2070. Six different desktops with no issues at all.

---

### Post by mastablasta on 2019-10-17
run a few tests using phoronix test suite to see if specific setting is causing the issue or just that demanding stuff can't be processed (in which case Autodave could be right and there is something wrong with card)

---


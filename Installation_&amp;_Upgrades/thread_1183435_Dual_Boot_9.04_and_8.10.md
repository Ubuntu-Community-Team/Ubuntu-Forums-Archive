---
title: "Dual Boot 9.04 and 8.10?"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by optimarcus_prime on 2009-06-10
Hi all,
So I've come to terms with some facts about 9.04 and 8.10:

-9.04 can run my Wacom tablet, dual monitors, visual effects, and most all things like a dream
-9.04 absolutely fails when it comes to running World of Warcraft (ATI Technologies Inc M52 [Mobility Radeon X1300] not supported by the ATI drivers in 9.04 booooo)
-8.10 can run World of Warcraft decently, at least enough for me to play
-8.10 can't run my Wacom tablet, dual monitors, or visual effects very well

So, in light of these terms, I've decided that I would like to attempt dual booting 9.04 and 8.10.  Ideally, I would like to do this with one home folder on a separate partition, so that both installs can access the same information.

Now, before I get all into this process I have to ask: Is this even possible? 

I know I can create a separate home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I know I can dual boot the system: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
(I would have to modify those instructions to work with an Ubuntu/Ubuntu system, rather than Ubuntu/XP.  Does anyone have a link to instructions for doing that?)

The big question is: Will it work?  I'm concerned that the two systems, with differing video card drivers and visual setups, would coiuld issues as far as sharing configuration files and things like that.

I'm also open to suggestions for a better solution to my problem, but at the moment this seems like the best option.  Thoughts?

Thanks!

---

### Post by presence1960 on 2009-06-10
not a good idea to share /home between two OS. A dual boot would work with no problem. Better to let each have their own config files. Each won't affect the other that way.

P.S. I know from bitter experience, it is a losing battle.
     I triple boot Ubuntu 9.04/Hardy 8.04/XP. 9.04 is my main OS and has a separate /home partition. Hardy is installed on one partition (no separate home) They run flawlessly since each has their own /home and config files.

---

### Post by dE_logics on 2009-06-10
If you have an ATI card, forget 3-d...that's what I say...I cant even CAD!

Yeah obviously you can, GRUB does the job automatically (sadly, the automation is not well in Gentoo :-().

---


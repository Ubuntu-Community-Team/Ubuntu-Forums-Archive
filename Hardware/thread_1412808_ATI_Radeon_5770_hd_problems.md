---
title: "ATI Radeon 5770 hd problems"
date: 2010-02-21
forum: Hardware
---

### Post by martinator35 on 2010-02-21
Ive got the 64bit version of Ubuntu Karmic and ive tried and tried to install the proprietary driver correctly, but have still not succeeded. Right now my computer will boot into a desktop environment, and i can run applications but the windows don't refresh. its like things go on in the background but they dont update. for example if i use alt+f2 to run a program, if i type into a field i dont see anything but when i hit enter it will do whatever i told it to. please help.

---

### Post by martinator35 on 2010-02-22
Also, i had installed kde as well to see what that would be like, i tried starting a session in kde and kde works just fine. So i think it is some kind of problem with gnome.

---

### Post by chronniff on 2010-03-03
what version of the driver are you using, I have been having major issues with compiz and the latest driver 10.2 on my 5770....10.1 works reasonably well, try installing that one (after first uninstalling the current one) and see what happens, if it still doesn't work give me some more details on what's happening, maybe I can help

---

### Post by SeePU on 2010-03-05
You guys should also mention/list what x.org and in particular, WHAT X-SERVER VERSION you're using or have installed.  I have read that 1.7 isn't compatible yet with Ubuntu or any Linux distro right now WITH ATI's fglrx driver.  I assume it would apply to 10.2 but don't quote me on that.

Carry on... :)

P.S.  I'm in the market for a new GPU and considering/comparing the HD Radeon 5770 to a Nvidia card, maybe 250 GTS or 260 GTX.  Which one should I pick?  Are your card problems really annoying?  How often do problems crop up?

I was concerned that there would be issues every time that X.Org is upgraded and/or the kernel is upgraded.

---

### Post by chronniff on 2010-03-05
SeePU.......your absolutely right about xserver 1.7 not being supported yet, so that could be an issue, one that has been bugging people for a while now (especially it seems arch users). thankfully I haven't had a need or an urge to install the latest xserver......

As for your question about what new gpu to get.....I was in your shoes only about 3 months ago when I went with the hd5770 after considering the performance you get for the low price, (not to mention an updated technology).....the hardware itself is impressive for its price and power usage.  I briefly tested it on windows 7 and it kept up with virtually any 3d rendering I threw at it (and actually 3d gaming hasn't been an issue at all on ubuntu either with this card)...the problem is with the driver support on linux.  The card is so new that to opensource drivers and at least around 6 months away from offering any kind of decent support, and even the ATI driver is still catching up the raedon 5xxx series' features. Catalyst 10.2 was the first in the 3 driver releases (while I have had this card) that really screwed me as far as completely breaking compiz and leaving my system almost unusable until reverting to 10.1 (although video tearing under compiz is quite common on all the releases I have tried unfortunately)......As of right now every logical part of me would tell you to definitely go with nvidia whose driver just seems to work out of the box.....however ati is completely rewriting the 2d rendering under X, plus a bunch of other stuff is now starting to come of age under the ATI fglrx driver.

So the short answer is nvidia definately the better and more stable choice right (only because their driver is much more mature and stable)....but in a couple months that could be completely opposite...If you can manage I would wait 2-3 months to see if this new 2d rendering is going to be the cure for all the video tearing and small yet frustrating issues.  Once those issues are fixed, the 3d performance which is already impressive will get its chance to shine.  The new 2d rendering method was included in 10.2, but not turned on yet

---

### Post by markbuntu on 2010-03-06
Right now it is a tossup. Nvidia's latest driver is melting cards while the ati driver seems to be a little slow in getting updated for the latest xservers and kernels but  will be fixed in a few months. I would rather go with a late driver than one that kills hardware. 

Nvidia definitely has more problems in the hardware reliability area, and admitting that they have a problem, especially with notebooks and the whole 8xxx and 9xxx series which have high failure rates. 

This is why so many new notebooks are sporting ati gpus.

---

### Post by SeePU on 2010-03-07
Thanks for those replies, guys!  Such a tough call!!

I'm leaning towards two or maybe three options;
1) just wait and keep using my GeForce 7950GT
2) I can get a significant upgrade for cheap, some Nvidia 9800GT cards can be had for around $80 and some used ones become available once Fermi cards are officially released.
2a) I will call this one 2A as I could do option #2 and buy a Radeon HD 5770 later on if I want based on ATI drivers maturing

I think the recent Nvidia driver fiasco may be some genius who looks after QC for the drivers not recognizing a setting that shuts off the fan or turns it down too low?  Some Nvidia cards from 260 GTX and up (probably the higher model ones are worse) would be the hardest hit?  Some of those get high temps.  I could be wrong, of course, but that is my theory.

chronniff, I had the same thinking: the 5770 is good for low temps/power and for the price, it seems like a good deal.  Sure, some Nvidia cards do better but need more power to do it.  Which one do you have?  I read about them having two types now, reference cards with full-sized shrouds and the egg-shaped one that some testers say lower the temps and wattage by a few degrees and watts, respectively.  I also don't know which brand since I've never shopped for an ATI card before.  In fact, I've only bought used cards before so shopping for a card is new for me...haha.  Anyway, thanks for the two perspectives, guys!   Is ATI cards okay for Wine yet or is that another area that needs more work from developers?

---

### Post by LoloftheRings on 2010-04-03
Please think twice before saying Nvidia sucks because of a bbq loving beta driver.. Nvidia has been making me happy since I have this new pc. If I had not been using ati before, I would have bought a brand new ati card. The point is, ati's proprietary drivers are not as good as the nvidia ones. Face it.

Wine  is a nvidia lover as well. I had lots of framedrops with ati where nvidia is a lot more consitent.

My temperature (gts 250) is about 30 C when idle, 40 C when gaming, and 50 C when running unigine heaven benchmarks. The card is overclocked so I'm sure it can run on lower temps. The temperature never goes about 60 C.

Ati is also pretty behind on supporting X versions, meaning you have to double check every update which makes you wanna throw your cup of coffee out of the window.

I say: Nvidia is the way it's meant to be played. Really.

---


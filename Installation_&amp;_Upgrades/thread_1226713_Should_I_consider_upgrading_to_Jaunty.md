---
title: "Should I consider upgrading to Jaunty?"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Volt9000 on 2009-07-29
I've been running 8.10 happily for a while now, and it's working the way I want. Jaunty Jackalope has been out for awhile and I'm hearing good things about it. At first I was hesitant to upgrade because it was so new, and I remember that setting some things up initially on this machine took a bit of work and sometimes were a pain in the ***, and I really don't want to go through that again.

So I'm wondering, is it worth it at this stage to upgrade to Jaunty? How stable has it become? Are there any major issues I should be looking out for? And if I decide to downgrade back to Intrepid Ibex, is that a simple task, or would I have to reinstall?

---

### Post by philcamlin on 2009-07-29
ugradng can be a pain so... doing a fresh install is better :)

jaunty has been great for me so far no issues at all! 

id do it but theres always that saying...

if it aint broken dont fix it :popcorn: its up to you :)

---

### Post by Chemical Imbalance on 2009-07-29
If I were you, I'd just wait 3 more months until Karmic comes out and do a fresh install then.

---

### Post by Volt9000 on 2009-07-29
Fresh install, really? Hmmm... :-|

I installed my home folder on a different partition than the root specifically to avoid a fresh install, since a lot of people seem to recommend it's easier to up/downgrade this way. But now I'm being told I should just fresh install? :???:

---

### Post by Chemical Imbalance on 2009-07-29
Well, it's just my preference.  

I've had troubles in the past with upgrades.  

Go for the upgrade if you like.

I still recommend waiting until Karmic if Intrepid is working fine.

---

### Post by merlinus on 2009-07-29
Actually, having /home in a separate partition makes installing newer versions mcuh easier, as you simply use that partition with its existing filesystem but do not format it.

---

### Post by Volt9000 on 2009-08-03
Really? Why Karmic over Jaunty? Won't the latter have longer support anyways?

---

### Post by slakkie on 2009-08-03
A bit offtopic, but why?? do people advise fresh installations over upgrading?? 

I have been upgrading all my Ubuntu PC's from version 5 (when I started with Ubuntu). I've had **one** problem when upgrading from 8.04 to 8.10 on the day 8.10 got released. Reinstalled 8.04 (who needs backup eh?!) a couple of days later. It was an Intel driver issue in xorg, pretty crucial on a desktop.But I would have had that problem even if I did a fresh install.
If I would have done that upgrade now I would not have any problems.

I don't get why installs are prefered over upgrades and really think it is bad advice to give. 

More ontopic:

I've just upgraded from 8.04 to 9.04 (too see how it works) and so far I'm pretty OK with it. I use KDE, so my experience might differ from yours as I'm using that for 3+ years now and hardly fire up gnome.. I upgraded to 8.10, but as soon as my PC came back up and booted 8.10 I upgraded to 9.04. (KDE4 replaced KDE3 in 8.10 so a huge change for me). But so far its all good.

If you have the space on a seperate partition, backup  your / dir with clonezilla (clonezilla.org) and upgrade your OS. If it fails, restore the backup and you are back in 8.10 land. I did this to go back to 8.04 if I end up not liking jaunty.

I think you could upgrade to Jaunty, in 8 months time your distro becomes EOL and you need to upgrade anyways to Jaunty. Why not do it now? Jaunty becomes EOL in 14 months. And then you can upgrade to Koala. I would do the upgrade now, or in about 2 months from now. You need to do it sooner or later.

---

### Post by Mark Phelps on 2009-08-04
One thing to consider is that if you're using an ATI video chip/card, and it's not one of the newer HD 3x or HD 4x series, you will no longer be able to get restricted drivers.  You will have to use the open source drivers and do without 3D hardware acceleration.

I have one of those "legacy" cards and there were rumours that AMD would restore support with Catalyst 9.7, but in checking that recently, I've seen no such support.  I think AMD's original release notes that said they would no longer be updating their legacy card drivers is the more accurate statement.  Which means, that there will be no restricted driver support in 9.10, either.

---


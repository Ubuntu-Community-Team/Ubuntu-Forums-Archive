---
title: "sound card sound blaster awe-32"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by p5344swan on 2007-09-23
Am New To Ubuntu And I Am Unable To Get The Sound Card (isa/sound Blaster Awe-32) To Work
Looked On The Internet And Found A Lot Of Info On Getting The Card To Work, But Did Not Understand Much Of The Material Because It Was Written For Those With A Better Understanding Of Linux Based Software. Also if the amount of pain involved in getting my old card to work is greater than the $20 for a new sound card please advise. Thanks

---

### Post by mrgoodkat on 2007-09-24
I'm kinda wondering the same thing myself with my newish X-Fi (Platinum) card... There's absolutely no support.

But your card is a fairly older one, have you been to this web site?

[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

You might be able to find more information there.

Reply with the final outcome!

---

### Post by kostkon on 2007-09-24
> **p5344swan said:**
> Am New To Ubuntu And I Am Unable To Get The Sound Card (isa/sound Blaster Awe-32) To Work
Looked On The Internet And Found A Lot Of Info On Getting The Card To Work, But Did Not Understand Much Of The Material Because It Was Written For Those With A Better Understanding Of Linux Based Software. Also if the amount of pain involved in getting my old card to work is greater than the $20 for a new sound card please advise. Thanks


Old ISA based cards are not automatically recognised any more. That's why you card does not work, despite the fact that there is a driver for it built into the Linux kernel. 

This [how-to at the Ubuntu wiki]("https://help.ubuntu.com/community/HowToSetupSoundCards") could help you to set up your card. You said that you had some problems following Linux how-tos, thus if you have any question about this how-to, don't hesitate to ask here.

The last resort should be buying a new card. It is a fact that your card is very old, and especially it is using the *ISA bus*, so yes, buying a new *PCI* sound card would be a reasonable thing to do.


> **mrgoodkat said:**
> I'm kinda wondering the same thing myself with my newish X-Fi (Platinum) card... There's absolutely no support.

But your card is a fairly older one, have you been to this web site?

[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

You might be able to find more information there.

Reply with the final outcome!

Indeed, there isn't a Linux driver for *X-Fi* cards yet. *Creative* is supposed to supply a beta version of the driver at the last quarter of 2007. Supposedly, the reason for the delay of producing a driver, is that *Creative* spent many resources for producing a driver for *Vista* and it didn't have any time to produce one for Linux.

---

### Post by mrgoodkat on 2007-09-24
I think it'll be worth the wait because they are damn good cards. I'm running Ubuntu from my laptop at the moment though so it's really nice for sound to be supported out of the box.

Love your profile avatar by the way, huge fan of the Lion King :D

---

### Post by kostkon on 2007-09-24
> **mrgoodkat said:**
> I think it'll be worth the wait because they are damn good cards. I'm running Ubuntu from my laptop at the moment though so it's really nice for sound to be supported out of the box.

Say it big coincidence, but yesterday when I posted here saying that *Creative* will soon release a beta driver, [the same day it happened]("http://connect.creativelabs.com/linux/default.aspx")!!

It is only for *64bit* kernels. I suppose *Creative* will provide a *32bit* version pretty soon.

If you have a 64bit Ubuntu you can try it. Just read the release notes for the driver, for instructions on how to install it. If you wait some days, I am sure some articles will pop-up at various sites about the driver, and you can find if it is working fine before you try to install it.

> **mrgoodkat said:**
> Love your profile avatar by the way, huge fan of the Lion King :D

Thanks very much!! :) I am too a big fan of the movie!! It rocks!! :popcorn:

---


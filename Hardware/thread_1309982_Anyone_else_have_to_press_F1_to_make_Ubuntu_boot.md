---
title: "Anyone else have to press F1 to make Ubuntu boot"
date: 2009-11-01
forum: Hardware
---

### Post by mjp29 on 2009-11-01
I have installed Ubuntu on 4 computers.  Three of those four computers will just boot right into Ubuntu.  However, one of the Ubuntu computers [the Dell desktop], I have to press F1 after starting/power up the computer to then force the computer to continue booting into Ubuntu.

Anyone else have to do this?

Could it possibly be caused by the way I've placed the jumper on the HD?  I don't think so, as I've tried several combinations on the HD [as far as switching the jumpers goes]

---

### Post by coffeecat on 2009-11-01
Before I even googled, I thought that this sounded like a BIOS issue. (Dell are weird anyway.) I had only to type "dell f1" into the google search field, and it prompted me with "dell f1 to continue" with over 260,000 results - you are not alone. :p

[This was the first hit]("http://forums.techguy.org/hardware/512521-how-get-rid-post-pause.html"), with the suggestions to reset the CMOS and update the BIOS being the most sensible, imo. I would go for the CMOS reset first. Anyway, if nothing there helps, try googling that string.

---

### Post by mjp29 on 2009-11-01
> **coffeecat said:**
> Before I even googled, I thought that this sounded like a BIOS issue. (Dell are weird anyway.) I had only to type "dell f1" into the google search field, and it prompted me with "dell f1 to continue" with over 260,000 results - you are not alone. :p

[This was the first hit]("http://forums.techguy.org/hardware/512521-how-get-rid-post-pause.html"), with the suggestions to reset the CMOS and update the BIOS being the most sensible, imo. I would go for the CMOS reset first. Anyway, if nothing there helps, try googling that string.


Well, thank goodness.

A follow up question: Is it an issue with Ubuntu or generally speaking does it occur with ms windows to (maybe moreso) - ?

One thing I'd like to add is that I used an HP desktop (still do) for a month or so with Ubuntu and there was one specific problem with it that was common with HP desktops.  However, the Dell laptop and Dell Desktop have given more fits than the HP ever did.  I do believe it is the way that specific manufacturers program the BIOS.  Noteworthy, however, is this Dell ran ms windows xp for years and I never I had to hit F1 to get booting started.

Another thought is that at some point when I was upgrading an old Mac G4 cube to os X [it had os 8 or 9.x on it for years] I had to at one point upgrade the BIOS.  There were stern warnings that doings so there was no going back (if one did so there was no way to install os 9.x and use it ever again).  So it appears BIOS can be changed [but is a more permanent change].  One would think that possible the Ubuntu programmers/developers could consider a standard BIOS upgrade for users like me, that only us Ubuntu and no ms windows, to standardized the BIOS to work with Ubuntu & do away with all these non-standard BIOS programmed in by various manuafacturers (Dell, HP, etc...).  It could be done.  But I'm sure many users still partition a place on their hard drives for ms windows, which is one reason there may be no movement to do so.  However, there could be a BIOS upgrade that wipes out manufacturers BIOS but it would be a one way street - stern warnings could be made that you can do this to standardized the BIOS for Ubuntu only but you will not be able to run ms windows versions on your computer.

---

### Post by coffeecat on 2009-11-01
> **mjp29 said:**
> One would think that possible the Ubuntu programmers/developers could consider a standard BIOS upgrade for users like me, that only us Ubuntu and no ms windows, to standardized the BIOS to work with Ubuntu & do away with all these non-standard BIOS programmed in by various manuafacturers (Dell, HP, etc...).

The BIOS has absolutely nothing to do with the operating system, and vice versa. The BIOS is chosen by the motherboard manufacturer, so you should be sure to get a BIOS upgrade **only** from the manufacturer of the motherboard. In the case of Dell, with custom-made motherboards, I guess you would need to get a BIOS upgrade from them. Writing a BIOS is a very specialised business, and there are only a few companies doing this, which is why you'll never see an Ubuntu BIOS - or a Microsoft one for that matter.

In your case the BIOS is causing problems long before Ubuntu is starting up. In fact before grub loads. So your BIOS problem has nothing to do with Ubuntu. The fact that it manifested when you installed Ubuntu is probably a coincidence. Have a look at the Google hits. Most of the people getting the F1 problem are running Windows.

But before you do a BIOS upgrade, research carefully why other people are getting this. As I said, a simple CMOS reset may do the trick. And if you really need to update the BIOS, take care. You can completely brick a machine if it goes wrong.

And good luck!

---

### Post by cmcanulty on 2009-11-01
I have a dell inspiron 9300 laptop and it upgrades to karmic and then reboots and says only partial install, this has happened 3 times. i may do a clean install but it was a nightmare getting wireless working so i hesitate

---

### Post by Johnny2good on 2009-11-01
No probs here i installed it on a Dell Vostro 1000 and everything works fine i put Fedora 11 on it before that and it crashed like 100 times gurrr but have 2 say Ubuntu 9.10 rocks happy days :popcorn:

---

### Post by mjp29 on 2009-11-01
> **coffeecat said:**
> The BIOS has absolutely nothing to do with the operating system, and vice versa. The BIOS is chosen by the motherboard manufacturer, so you should be sure to get a BIOS upgrade **only** from the manufacturer of the motherboard. In the case of Dell, with custom-made motherboards, I guess you would need to get a BIOS upgrade from them. Writing a BIOS is a very specialised business, and there are only a few companies doing this, which is why you'll never see an Ubuntu BIOS - or a Microsoft one for that matter.

In your case the BIOS is causing problems long before Ubuntu is starting up. In fact before grub loads. So your BIOS problem has nothing to do with Ubuntu. The fact that it manifested when you installed Ubuntu is probably a coincidence. Have a look at the Google hits. Most of the people getting the F1 problem are running Windows.

But before you do a BIOS upgrade, research carefully why other people are getting this. As I said, a simple CMOS reset may do the trick. And if you really need to update the BIOS, take care. You can completely brick a machine if it goes wrong.

And good luck!

I thank you so much for kind reply and if I may reply kindly.  I know that in forums [and email] it is often misconstrued as the tone the person is talking in- as it is all text.  Let me make it clear here that I'm not arguing, I'm kindly pointing out some things as you did - so Ubuntu to both of us!  [humanity towards others!]  I am kindly replying and just talking to you below - not flaming you or anything like that - I am a VERY nice person and please take this reply below as a nice reply as if we were sitting at a bar next to each other just cordially talking about things while drinking a beer or two.

You said the BIOS has absolutely nothing to do with the operating system. You said the BIOS is chosen by the motherboard manufacturer.  You suggested that I or anyone get their BIOS upgrade from the motherboard manufacturer.

I know that this is usually and generally the case with PC's; however, if you recall, I was speaking from a standpoint of an Apple G4 Cube user.  The difference here is more distinct and very different.  Let me explain below.

Apple computer controls both the hardware and the operating system, unlike PC.  In fact, legally, Apple both sells the hardware box (the Mac) and has total control over the operating system on their box (the Mac operating system).  Apple does indeed control the BIOS, the hardware, and the operating system.  The BIOS on an Apple Mac is not chosen by some random motherboard manufacturer.  The BIOS on an Apple Mac is dictated by Apple.  The BIOS on an Apple is standardized.

When I was an Apple user I did not go to the manufacturer of the motherboard in my Mac to get my BIOS upgrade.  I went to Apple.  There was no need to go elsewhere because Apple controls their entire hardware, operating system, and BIOS on their computers.

I know it is confusing concept for many to wrap their mind around as there are so many more PC's in the world with ms windows on them.  However, there is one company, called Apple, that still controls their hardware, their OS, and their BIOS.

But let's think about this.  Many of us think that Apple is a like a dictatorship, as they control their hardware and their operating styem upon booting the computer.

Let's think about this a step further.  We as Ubuntu users, strive to control our computers ourselves and not rely on ms for their operating system or any particular manufacturer for our hardware [be it motherboards or what have you].

Twenty years ago most computer companies sold and delivered their operating system on the system they were selling (remember the Commodore vic-20, the c-64, the TI-44A, the Tandy CoCo, IBM PC & PC jr., the Apple II, the Timex Sinclair, The coleco-vision computer adapted keyboard, the list goes on).

There is only one viable computer company left that still delivers the hardware and the o.s. and that is Apple.

But philosophically, as Ubuntu users, we strive to have a free open source operating system today and now.  

Why shouldn't users like me that want a standard BIOS now not atleast be able to over-write the motherboard BIOS if we choose to not want to ever run ms windows on our system ever?

It's a philosophical argument.   But we can as an Ubuntu community decide that we will run only on our computer the way we want to (only install the operating system Ubuntu Linux).  We could also choose to over-write the BIOS of any and all motherboard manufacturers, as Apple has proven can be done regardless of who Apple chooses to make their motherboards, with our own Ubuntu BIOS if we choose to run only Ubuntu (as on Apple hardware only os x can be run).

Apple has total control of their hardware, their os, and their BIOS.

As Ubuntu users, why can't we choose to have total control of the same things?

After all, we are open source.

Think about it.


p.s. I re-read this post and I did not mention I was an Apple user in the original post, so I apologize to the person that replied - my mind was bouncing around to a post I made before, however; the info. in the post above still reflects my thoughts.  Sorry.

---

### Post by whizbang121 on 2009-11-01
I have a similar problem on a Dell desktop.  Didn't happen with 9.04.  I press f12 and scroll down to 'boot from C drive' rather than 'normal' which is number 1.  Then bootup proceeds normally.

> **mjp29 said:**
> I have installed Ubuntu on 4 computers.  Three of those four computers will just boot right into Ubuntu.  However, one of the Ubuntu computers [the Dell desktop], I have to press F1 after starting/power up the computer to then force the computer to continue booting into Ubuntu.

---

### Post by BackwardsDown on 2009-11-02
> **mjp29 said:**
> I have installed Ubuntu on 4 computers.  Three of those four computers will just boot right into Ubuntu.  However, one of the Ubuntu computers [the Dell desktop], I have to press F1 after starting/power up the computer to then force the computer to continue booting into Ubuntu.

Anyone else have to do this?

Could it possibly be caused by the way I've placed the jumper on the HD?  I don't think so, as I've tried several combinations on the HD [as far as switching the jumpers goes]

Old computers have that a LOT. The BIOS has a battery so it can for example let the internal clock run even when the computer is off. Changing the battery (its allways a normal wrist-watch-battery, a flat one) with a new one will 95% fix the issue.

There is a lot of information about it on google.

PS:
Try to boot it with a live-cd without an internet connection. If your clock is reset, you're sure its your bios-battry

---


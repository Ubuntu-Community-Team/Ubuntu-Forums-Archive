---
title: "Install New nVidia GeForce 6200 256MB PCI?"
date: 2009-12-30
forum: Hardware
---

### Post by JSeymour on 2009-12-30
Hi All,

Ubuntu 9.10 Desktop on a Dell 1600SC.  Got an nVidia GeForce 6200 256MB PCI card on the way.  Have lots of experience with Sun Sparc boxen, but none with tricking-out Wintel ;) hardware.

The machine has an on-board ATI Rage XL graphics adaptor.  So the 1st question is: Need I do anything special wrt to that, or just move the monitor cable over to the nVidia card and fire 'er up?

Next I suppose I'd want to install the nVidia drivers? (nvidia-glx-185 what I want?)

Then do one of the (successful) procedures outlined in the [nvidia settings can't save to conf file]("http://ubuntuforums.org/showthread.php?t=1101445") thread to get it configured?

Btw: I see a Synaptic listing for "nvidia-settings," but none for "nvidia-xconfig," and neither currently resides on my system.  Whence nvidia-xconfig?

Thanks In Advance,
Jim

---

### Post by JSeymour on 2009-12-31
Somebody?  Anybody???  The card arrived today, so some guidance by, oh... say... tomorrow morning, U.S. eastern time, would be terrific :).

Or I'll just wing it...

---

### Post by lindsay7 on 2009-12-31
If the graphics card that is on the computer is on the motherboard, you do not need to do anything except add the new pci card and connect the cable to it.  When you start the computer with Ubuntu is should start up with the standard graphics. Once it is up and going go to System/Administration/hardware drivers. You will see the drivers that are available and also the recommended driver. Pick the recommended one and restart your computer.

After that you can go to the Nvidia setting under Administration and check the resolution. It should default to auto.

---

### Post by JSeymour on 2009-12-31
> **lindsay7 said:**
> If the graphics card that is on the computer is on the motherboard, you do not need to do anything except add the new pci card and connect the cable to it.
Interesting.  Some people, elsewhere, a couple elsewheres, actually, say I *do* need to disable the on-board adapter before re-starting with the new card, others, such as you, say I do not.  One of the do-not-have-to's, when I asked if the system continuing to "talk" to the inactive adapter won't slow the new, faster one down said I would need to "disable" the inactive adapter in xorg.conf (which, btw, currently does not exist!)

I'm so confused... :confused:

Thanks,
Jim

---

### Post by lindsay7 on 2009-12-31
I have built three computers in the past year which all had onboard graphics.  I put in Nvidia graphic cards on all of them and have never had to do anything about disabling the onboard graphics.  By the way on of my cards is a pci, on is a pci-e and one is an AGP.

My guess is that when Ubuntu sees a graphics add on card it defaults to that setting and auto disables the onboard graphics.  The reason I say this is that once the new graphics card is in place. The onboard gpaphics do not work as long as the add on card is installed. I have checked to see if this is the case.

Anyway, you will not hurt anything by adding the new card and seeing if what I have said is the case.

---

### Post by JSeymour on 2009-12-31
Thanks for the info, Lindsay7.  It's very helpful.

Btw: nVidia drivers: 190 or 195?  Near as I could tell, 195 was still in Beta?

Jim

---

### Post by ratcheer on 2009-12-31
> **JSeymour said:**
> Thanks for the info, Lindsay7.  It's very helpful.

Btw: nVidia drivers: 190 or 195?  Near as I could tell, 195 was still in Beta?

Jim

I have been using 195.22 for a couple of weeks with no problems, at all. There are even newer ones than that, though.

Tim

---

### Post by JSeymour on 2009-12-31
> **ratcheer said:**
> I have been using 195.22 for a couple of weeks with no problems, at all. There are even newer ones than that, though.

Tim
Thanks for the feeback.  Yeah, .30 is what's in the repo now.  I believe that's the way I'll go.

Jim

---

### Post by lindsay7 on 2009-12-31
I have the same card. The 195.3 driver will install by itself.  See screen shot.

[ATTACH]141910[/ATTACH]

---

### Post by JSeymour on 2009-12-31
Well, that was a fail :(

It turns out that, due to some brain-deadness in the Dell 1600SC BIOS, few add-on graphics cards will work.  It turns out the shiney new nVidia GeForce 6200 is not one of them :(.  In fact: Apparently very few, if any, nVidia cards will work on a Dell 1600SC.  The BIOS is smart enough to disable the integrated graphics controller, all right, but the add-on card simply fails to work.  Other graphics cards work interrmitantly, or exhibit undesirable behaviour if they do work.

So far the only "modern" card that is reported to work well is the ATI Radeon 2400 HD Pro.  I was really hoping to go nVidia, because, from all I've read, they have much better Linux support.

Edit: I don't get it.  Somebody said that card worked, but the ATI page says it's PCI-E, and the PE 1600SC has no PCI-E.
Edit: Okay, ATI's site is brain-dead.  There *are* PCI versions. :rolleyes:

Boy, am I ever **ticked** at Dell right now :x

Jim

---

### Post by JSeymour on 2010-01-06
Just for reference: Did further research, found a couple people that claimed an ATI Radeon HD 2400 Pro would work.  Found them for a good price at Tiger Direct.  Ordered.  Got it.  Installed it.  Works like a champ :).

Still annoyed with Dell, tho.

Jim

---

### Post by cascade9 on 2010-01-07
> **JSeymour said:**
> Well, that was a fail :(

It turns out that, due to some brain-deadness in the Dell 1600SC BIOS, few add-on graphics cards will work.  It turns out the shiney new nVidia GeForce 6200 is not one of them :(.  In fact: Apparently very few, if any, nVidia cards will work on a Dell 1600SC.  The BIOS is smart enough to disable the integrated graphics controller, all right, but the add-on card simply fails to work.  Other graphics cards work interrmitantly, or exhibit undesirable behaviour if they do work.

So far the only "modern" card that is reported to work well is the ATI Radeon 2400 HD Pro.  I was really hoping to go nVidia, because, from all I've read, they have much better Linux support.

Edit: I don't get it.  Somebody said that card worked, but the ATI page says it's PCI-E, and the PE 1600SC has no PCI-E.
Edit: Okay, ATI's site is brain-dead.  There *are* PCI versions. :rolleyes:

Boy, am I ever **ticked** at Dell right now :x

Not the 1st time I've seen dell 'locking' BIOSes so you cant use whatever video card you want. I've heard of people flashing out the stock dell BIOS with a generic BIOS for whatever chipset the computer is running, and that has worked in the past. Probably more effort, and risk, than you want to go to now seeing how you actually have a running card, but it worth remembering IMO. 

Id be more than 'ticked off' at dell...but things like this are just one reason why I build my own computers.

---


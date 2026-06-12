---
title: "Video card to bypass 82845 controller"
date: 2010-11-11
forum: Hardware
---

### Post by egeezer on 2010-11-11
I'd like to install some PCI card that would enable me to run Lucid (or any other distro with strong graphics demands) on my ancient Compaq.  It has the dreaded G82845 graphics controller, which seems to be incompatible with anything newer than an abacus.:lol:
Problem is, I don't know whether the 82801 PCI bridge (2003 vintage) will handle modern PCI cards.  Anyone have experience with this, or a good place to look for help on the specific bridge?  I don't that computer for major stuff, so it's not an urgent issue, more like an interesting challenge.
Thanks in advance for any suggestions!

---

### Post by egeezer on 2010-11-12
*Bumped* following extensive edit - asking the question again in a different form

---

### Post by Yellow Pasque on 2010-11-12
Get a Geforce 8400GS PCI card.

---

### Post by egeezer on 2010-11-14
Thanks for the suggestion, it led me to the right places.  I don't think the 8400 will work, because it's DDR2 and my old box runs plain DDR.  However, I might be able to track down a 5200, which is DDR.  Discontinued, I believe, but probably could find a dusty old one sitting around somewhere.  Still don't know about the bridge.

---

### Post by Yellow Pasque on 2010-11-14
The RAM on the graphics card has nothing to do with your system RAM. Try the 8400.

---

### Post by egeezer on 2010-11-14
Well, dang!  I had no idea of that - thanks!  I'll give it a shot in the next few days and see how it goes.  And thanks for the replies - this is the first time I've tried messing with hardware other than memory, so it's all new to me.

---

### Post by egeezer on 2010-11-17
One last (I hope!) question: does the card automatically disable the integrated 82845 graphics controller, or does that have to be done manually?

---

### Post by Fafler on 2010-11-17
It should work out of the box. But we'll fix it if it doesn't.

---

### Post by egeezer on 2010-11-17
Wow, Fafler!  That's the best news I've heard!  And my special thanks for the reassurance.  Now I anxiously await the UPS delivery so I can do my first actual hardware meddling.

---

### Post by cascade9 on 2010-11-20
> **egeezer said:**
> One last (I hope!) question: does the card automatically disable the integrated 82845 graphics controller, or does that have to be done manually?

Depends on the BIOS. 

Before you install the card, checkm in your BIOS to see if you can change the video from 'onboard' to 'PCI'. 

If you've having issues finding that setting, or dont know if its even there, you could post your motherbaord model.

---

### Post by egeezer on 2010-11-21
Aha!  Thank you very much, cascade9!  I found the setting, and I'll surely change it before I install.  I'd feel a lot more comfortable doing that than relying on the Plug and Play function to handle it.

---

### Post by cascade9 on 2010-11-22
No problem, good luck with upgrading :)

---

### Post by egeezer on 2010-11-25
Well, dang again!  I find my power supply is only 250 watts, and the 8400GS card requires 300.  Guess this machine will have to settle for running minimal OSs only.

---

### Post by egeezer on 2010-11-25
I'm bumping this to add a question that just arose at dinner:

I'm getting conflicting advice: one friend commented that if I'm just running lighter stuff like Compiz effects and no heavy gaming (I am not a gamer, that's for sure!) the power supply can handle it. Another says I'll fry the power supply for sure. Anyone else care to chime in? 

Don't worry - I won't blame anyone, I just want to get a few independent ideas!

---

### Post by Fafler on 2010-11-26
Don't worry. The 8400GS uses around 10 watts and will work with almost any PSU, They are just covering their rear ends.

---

### Post by egeezer on 2010-11-26
Well, thank you once again - that's a great relief!  I suspected it was that "product liability" sort of thing, but it's nice to know a bit more in advance.  So here we go!

---

### Post by cascade9 on 2010-11-27
> **egeezer said:**
> I'm bumping this to add a question that just arose at dinner:

I'm getting conflicting advice: one friend commented that if I'm just running lighter stuff like Compiz effects and no heavy gaming (I am not a gamer, that's for sure!) the power supply can handle it. Another says I'll fry the power supply for sure. Anyone else care to chime in? 

Don't worry - I won't blame anyone, I just want to get a few independent ideas!

Its always possible that even adding a low power device like a 8400GS could be the proverbial 'straw that broke the camels back' but its not likely. 

I agree with Fafler, nVidia is just covering thier butts. (though I'm not sure about 10watts, but it wouldnt be much past that if 10watts is wrong)

---

### Post by Fafler on 2010-11-27
I have a system with two Quadro NVS290 cards, which i basically a 8400GS with another BIOS, and if i remove one card, the idle power usage drops 10 watts. However, i'm not sure about load conditions, but it can be much more.

---

### Post by cascade9 on 2010-11-28
If you've got 10watts with a wall socket power consumption meter, it would be lower than that internally (due to the PSU not being 100% efficient). Probably in the order of 7-8watts. 

nVidia say that max power draw on a 8400GS is 71watts- 

> **Q: What are the power requirements for the GeForce 8400 GS GPU?**
A: GeForce 8400 GS cards have a maximum power draw of 71 watts. [http://www.nvidia.com/object/geforce_8400_Gs_faq.html](http://www.nvidia.com/object/geforce_8400_Gs_faq.html)

But I think that they are just being very conservative. Other places have different ideas about max draw, see here (19watts 2D 32watts 3D)- 

[http://www.tomshardware.com/reviews/geforce-radeon-power,2122-4.html](http://www.tomshardware.com/reviews/geforce-radeon-power,2122-4.html)

---

### Post by egeezer on 2010-11-28
Okay, I chickened out finally.  I'd be paying around $50 for the card and run some risk, however slight, of wiping out a perfectly usable old machine.  I  think I'll just leave well enough alone for now, and learn to get used to things like LXDE and XFCE and Fluxbox and...!

---

### Post by egeezer on 2010-12-12
Found a way around the low-wattage problem: I got a GeForce 6200 with 256MB DDR2, which specifies 50 watts less as a requirement.  Installed it, accepted the driver the Meerkat suggested, and I'm up and running.  :D

---


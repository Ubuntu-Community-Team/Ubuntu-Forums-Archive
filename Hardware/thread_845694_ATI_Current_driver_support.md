---
title: "ATI Current driver support"
date: 2008-06-30
forum: Hardware
---

### Post by rcsdnj on 2008-06-30
Hi,

I'm considering the possibility of seeling my Nvidia 7600GT card to buy an ATI x1650 Pro (or similar with the RXX series chip). This card seems to have a similar performance to mine and looks well supported (I was checking [this]("http://www.x.org/wiki/RadeonFeature") and [this]("http://www.x.org/wiki/RadeonProgram")) as references).

ATI has been looking currently more attractive by an open source viewpoint. But I'd like to know your opinion about this, and specifically about the following points:

- Vsync status. I've read in the forums about tearing problems. I'd like to know what can I expect for this aspect, both for 2D / 3D / video playing, in the cases you are using the Open Source driver and when you're using the FGRLX driver.

- Stability with the open source and fglrx driver. I've had a 9600XT some years ago. The open source driver was kind of incomplete and slow, but the closed one was so unstable that I remember that it was better to keep using the open source one.

- Suspend/resume functionality, also on both drivers.

Although my plan is to use the open source driver, it's important to know about the fglrx status as well, since if the open source driver is not "good enough" for some situation, I'll have the closed as an alternative. Choice is always good :)

Any comments / opinions about this will be very appreciated. Thanks in advance!

---

### Post by Rocket2DMn on 2008-06-30
Why would you sell your card just in order to put something similar in?  Are you having problems with the Nvidia card?  I would stick with that if it works, but if you really want to switch, go for it.  It seems to be that some of the cards in a x##50 series sometimes have problems, but you would just have to search the forums to see what sort of problems have come up recently.
Most people tend to recommend Nvidia over ATI for linux since they have a better history of playing nice, but ATI is getting better.

---

### Post by rcsdnj on 2008-06-30
Hi Rocket2DMn,

I like changing my system and testing it, so the idea of testing the open source drivers is interesting to me. Since I'm not a gamer I'd not be worried if the open source drivers have not "excellent performance"... but those 3 things I've pointed are very important, the "minimal reasonable set", and that's why I'm considering to try finding some answers to them before doing this move. I've searched about those points which I asked, but there are many different problems under different circumstances and it is hard to get precise conclusions. I think I may be lucky asking directly on what matters.

My Nvidia card currently works fine, but I don't like how Nvidia handles their products, without even releasing the specifications. AMD/ATI got a point on this. 

The main practical complaint I'd have about nvidia is that, when Xorg developers creates new features (like AIGLX, hardware video acceleration and the incoming kernel modesetting and Dri2), Nvidia comes very behind and takes a long time to be in pair (remember black window bug? And the white screen problem when switching VTs?). 

So I hope, if I really decide to switch, I'll at least have more driver options if using the ATI card. And having choice is nice :)

---

### Post by Rocket2DMn on 2008-06-30
Basically any ATI card that you buy these days will use restricted ati drivers, not the open source ones.  Open source ati drivers are used on cards older than the Radeon 9500.  You will be using the "fglrx" drivers with the x1650.

Nvidia has open source drivers, "nv", but aren't used much anymore.  There is also the option to use Nouveau open source drivers on Nvidia cards.  They are unofficial and I don't think they have 3d support yet, but are rather good otherwise (from what I hear).  Since you seem to enjoy this stuff, you might like to google around for more information on it.

---

### Post by rcsdnj on 2008-06-30
Thank you for your attention, Rocket2DMn. I've read about Nouveau, but they look too alpha at the moment. According to your report, I guess should wait a little more to see how ATI open source drivers evolve, too. Maybe I'll run the risk anyway (if I have a good opportunity to). In case I do this, I'll come here to try to give my $0.02 about the experience.

---


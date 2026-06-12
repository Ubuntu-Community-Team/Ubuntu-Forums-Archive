---
title: "Graphics issues with Nvidia 8500GT (x2)"
date: 2010-11-02
forum: Hardware
---

### Post by Musicalmidget on 2010-11-02
For a few years I was using an Nvidia 8800GT in my Ubuntu machine with dual monitors and no problems.  That card recently met an untimely end however and I've had to revert to using a couple of 8500GTs that were sat around spare.

While the 8500GT cards have dual outputs and can support a basic dual monitor setup through one card, I'm actually using two because I require both to be connected by DVI - connecting one through VGA is not an option in this case.

This is where I run into problems.  Both monitors will work correctly once the Nvidia drivers are installed but I am unable to enable even basic compositing.  That seems only to work when both monitors are connected through one card.

Is this a common issue or is there something I might have overlooked?

---

### Post by Fafler on 2010-11-02
Compositing?

Things like dragging from one monitor to another or having windows span more than one monitor only works with twinview and twinview only works on a single card. With two cardsm you have to use xinerama, which doesn't support these things.

---

### Post by Musicalmidget on 2010-11-02
I'm not sure if my terminology is slightly off but that is indeed what I mean.  Basically anything which attempts to enable the composite extension in X11.

I hadn't realised this stuff was only supported in TwinView but that makes sense based on the behaviour I have experienced.  Thanks for the explanation - I'll make do with what I have for now and will hopefully be able to replace those two cards with another dual DVI card in future.

---


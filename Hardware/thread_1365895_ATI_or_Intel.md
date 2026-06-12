---
title: "ATI or Intel"
date: 2009-12-27
forum: Hardware
---

### Post by joplass on 2009-12-27
Awhile back I had issues getting glx going with ATI because they did not give us much driver support like Nvidia for example.
I want to purchase a new laptop those with Nvidia graphic cards are out of my budget.  It leaves me with ATI and Intel to pick from.  Which of the two previous would you recommend?
Thanks

---

### Post by Magnesium on 2009-12-27
> **joplass said:**
> Awhile back I had issues getting glx going with ATI because they did not give us much driver support like Nvidia for example.
I want to purchase a new laptop those with Nvidia graphic cards are out of my budget.  It leaves me with ATI and Intel to pick from.  Which of the two previous would you recommend?
Thanks

IMHO, ATI's Linux support is still somewhat fragmented. There are two open source drivers and ATI's proprietary driver, all of which are good at different things and not good at others. My laptop has an old ATI radeon that was a big pain to set up (I still don't have some things working, like suspend). Now, the newer ATI cards might be easier to set up, but I still get the impression that ATI does not care about the Linux community. [-(

I've never had a computer with Intel graphics, but my Linux-using friends who have haven't had any big problems with them, and they were quite easy to set up, and more things "just work" with Intel.

So basically the ATI is more powerful, but Intel has better Linux support. :confused:

Mg

---

### Post by MeanEYE on 2009-12-27
I'd go with nVidia, but since you lack options with those cards... let me put it this way:

Intel has crappy drivers which don't have support for OpenGL > 2.1... Just terrible, you can't play anything and besides that, there's a know bug (at least was before Karmic) that would freeze your display just for fun.

As for ATI... that is a whole different level of malfunctioning drivers and bad support for us (Linux users). I've just spent 6 hours trying to make ATI 4670 graphic card to work with no luck. I've tried tons of drivers, manually compiling and configuring and nothing seems to work. 

A colleague from work had his share of ATI problems with totally different graphic card.

Like **Magnesium** said. ATI generally sux and doesn't care about Linux users. Intel had crappy support in Jaunty but they are a lot easier to set up. I have Toshiba U400-12R with Intel card. Basically everything worked like charm from the start except lack of OpenGL 2.1+ support and that stupid bug in Jaunty...

My advice is... INTEL. Crappy support for gaming, but usable and wont let you down like ATI. If you get a chance for nVidia... GO FOR IT!

---

### Post by joplass on 2009-12-28
Thanks guys.  I will probably have to spend extra on a Laptop with Nvidia.  I don't want a machine that doesn't do everything I want it to do.

---

### Post by cb951303 on 2009-12-28
ATI support currently sucks but it doesn't mean they don't care about linux community. ATI/AMD releases their card specs so that open source drivers can be written. Have you seen such an act with NVIDIA?

In brief, for now, save some money and buy a NVIDIA card.
In the future though, radeonHD driver will probably be the best supported graphics driver on linux.

---

### Post by Magnesium on 2009-12-28
> **joplass said:**
> Thanks guys.  I will probably have to spend extra on a Laptop with Nvidia.  I don't want a machine that doesn't do everything I want it to do.

My suggestion would be to invest in a laptop with nVidia graphics...you will have less troubles overall with that choice.

What is your budget? Maybe we can help you find a laptop with nVidia in your price range...

> **cb951303 said:**
> ATI support currently sucks but it doesn't mean they don't care about linux community. ATI/AMD releases their card specs so that open source drivers can be written. Have you seen such an act with NVIDIA?

In brief, for now, save some money and buy a NVIDIA card.
In the future though, radeonHD driver will probably be the best supported graphics driver on linux.

I see your point...what I meant was that ATI's *internal* Linux development (fglrx) is not very good, and is substantially below that of nVidia's internal development. Sure, nVidia's drivers are binary and closed-source, but they are so good that I don't need an open-source nVidia driver to be happy.

But I agree that the best option for joplass would be to save up some money and buy an nVidia powered laptop. I also agree that radeonhd may become the best driver, especially if ATI starts getting involved with its development:

[CENTER]*Involvement of hardware manufacturer + open source = super good driver* :guitar:[/CENTER]

> **MeanEYE said:**
> I'd go with nVidia, but since you lack options with those cards... let me put it this way:

Intel has crappy drivers which don't have support for OpenGL > 2.1... Just terrible, you can't play anything and besides that, there's a know bug (at least was before Karmic) that would freeze your display just for fun.

As for ATI... that is a whole different level of malfunctioning drivers and bad support for us (Linux users). I've just spent 6 hours trying to make ATI 4670 graphic card to work with no luck. I've tried tons of drivers, manually compiling and configuring and nothing seems to work. 

A colleague from work had his share of ATI problems with totally different graphic card.

Like **Magnesium** said. ATI generally sux and doesn't care about Linux users. Intel had crappy support in Jaunty but they are a lot easier to set up. I have Toshiba U400-12R with Intel card. Basically everything worked like charm from the start except lack of OpenGL 2.1+ support and that stupid bug in Jaunty...

My advice is... INTEL. Crappy support for gaming, but usable and wont let you down like ATI. If you get a chance for nVidia... GO FOR IT!

Well put MeanEYE...=D>

Mg

---


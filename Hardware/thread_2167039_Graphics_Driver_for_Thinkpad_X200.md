---
title: "Graphics Driver for Thinkpad X200"
date: 2013-08-12
forum: Hardware
---

### Post by sonniesonnig on 2013-08-12
Hey there,
I want to play Minecraft on my Thinkpad X200 with 12.04.
Ubuntu has no graphics driver installed, so its laggy as hell.

I already checked out the[ x.org]("http://www.x.org/wiki/IntelGraphicsDriver/") and [01.org]("https://01.org/linuxgraphics/"). On x.org I can't find any driver and on 01.org there is just a driver for 13.04 which is not campatible with 12.04.
I also found a downgrade on 01.org, but it won't start. Maybe its not made for the 13 installer?

Anyone got an Idea?

---

### Post by Yellow Pasque on 2013-08-12
> **sonniesonnig said:**
> Ubuntu has no graphics driver installed, so its laggy as hell.

It comes with intel driver pre-installed. Only proprietary drivers show in "Additional Drivers" and intel is all open-source. Post your /var//log/Xorg.0.log (use [ code ][ /code ] tags).

---

### Post by Ranko Kohime on 2013-08-12
I don't play Minecraft myself, but I've heard many people describe it as GPU-hungry.  I'm going to guess, by the available processors for that model that you're not going to be able to run it at any acceptable level.

---

### Post by sonniesonnig on 2013-08-13
> **Temüjin said:**
> It comes with intel driver pre-installed. Only proprietary drivers show in "Additional Drivers" and intel is all open-source.

Ah, okay. Mea clupa. :oops:

> **Temüjin said:**
> Post your /var//log/Xorg.0.log (use [ code ][ /code ] tags).

The whole log?

> **Ranko Kohime said:**
> I don't play Minecraft myself, but I've heard many people describe it as GPU-hungry.  I'm going to guess, by the available processors for that model that you're not going to be able to run it at any acceptable level.

This is interesting. MC looks like a game from the early 2000s but needs more GPU than Counterstrike Source. :p

---

### Post by Ranko Kohime on 2013-08-13
Games from the early part of the century looked better than that, you're thinking early-mid 90's.

A cursory glance at gameplay on Youtube tells me it's not going to be friendly to low-power GPU's, just by the way things render when the camera pans.  (See footage from ANY PS1 title, compared to Minecraft to see what I mean.)

---


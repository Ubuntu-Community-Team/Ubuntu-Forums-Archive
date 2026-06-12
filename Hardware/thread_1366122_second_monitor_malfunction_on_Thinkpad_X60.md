---
title: "second monitor malfunction on Thinkpad X60"
date: 2009-12-28
forum: Hardware
---

### Post by sparky2 on 2009-12-28
big hello to the Ubuntu Community ...

I have just installed 9.10 and generally it's all working well, except trying to display only on my second monitor, a Dell 24" (S2409W). 

I can display on both monitors at once, but this assumes the lower resolution for both screens, so the Dell only replicates the Thinkpad's 1024x768, and image is thus "strecthed" 

But when I toggle to display only on the dell monitor, either via System>Preferences>Display or via the Thinkpad Fn-F7 keys, both screens go black, the mouse freezes and it never times out / back to previous mode. Basically I have to power on/off to recover :confused:

The Thinkpad Fn-F7 keys cycle through three display modes (like most laptops do):
1. primary screen only
2. both screens simultaneously (at lower resolution)
3. secondary screen only 

I get modes 1 and 2 OK, but not 3 - the one I need ! 

By the way there's no hardware issue at play, because I can boot Windows XP on same hardware and can use Dell monitor as I want, no problems.

Suggestions ???

---

### Post by efflandt on 2009-12-28
Have you tried booting with the external monitor already connected and turned on?  That might tend to use the external monitor by default, or at least recognize it.

Are you using any non-standard video drivers or Xorg.conf file (which by default is not in 9.10)?

Look at X related logs in /var/log and see if anything in them jumps out at you.

---

### Post by sparky2 on 2009-12-28
> **efflandt said:**
> Have you tried booting with the external monitor already connected and turned on?

yes, its always connected and powered.

> **efflandt said:**
> Are you using any non-standard video drivers or Xorg.conf file (which by default is not in 9.10)

No just standard Ubuntu 9.10 install

> **efflandt said:**
> Look at X related logs in /var/log and see if anything in them jumps out at you.

getting too advanced for me now ... :confused:

thanks

---


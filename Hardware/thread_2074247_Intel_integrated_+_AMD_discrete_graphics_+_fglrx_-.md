---
title: "Intel integrated + AMD discrete graphics + fglrx - possible?"
date: 2012-10-21
forum: Hardware
---

### Post by G04t on 2012-10-21
Hi all,

I've been scratching my head over this one for a while. Another afternoon of poking around with the new 12.10 release (after giving up on 12.04) has left me with zero progress, so I thought I'd ask here.

In my desktop, I currently run an AMD HD7970 discrete card and also Intel integrated HD3000 graphics from my i5 2500K. 

I've been trying to get the 2 to play nice together in Ubuntu for a while now, but I've really hit a wall and I'm starting to wonder if what I want to do is even possible with the current state of Linux graphics drivers. 

My setup is:
1 x monitor running from HD7970 via DisplayPort
2 x monitors running from the HD3000 via onboard outs (1 x HDMI and 1 x DisplayPort).

The AMD card *is* capable of running all 3 monitors and I have run it that way, but because it will not clock down properly with more than 1 display attached, it gets very hot and very loud even when idling in the case I run it in. So to save on power/heat/noise, I've attached my desktop-only (ie. no heavy gaming) smaller monitors to the onboard outputs. Given I run a compact micro-ATX case that is very near my head, going back to "Ol' Leafblower" is not an option.

In Windows 7 this is completely seamless and painless to set up. Catalyst and the Intel graphics drivers don't interfere with each other and everything works wonderfully. This one of (few and far between) things I actually really love about Win7.

So my question is... is this even possible to achieve in Ubuntu at this time? Does fglrx (proprietary drivers) prevent this / is it possible with radeon?

Any ideas will be much appreciated :)

---

### Post by G04t on 2012-11-13
Sorry if it's bad form to necro my own thread, but since this is still an ongoing issue (and I'm still stuck on Windows for my desktop otherwise) I thought I'd see if anybody has had any ideas.

I've tried the method for hybrid graphics in this thread: [http://ubuntuforums.org/showthread.php?t=2083181](http://ubuntuforums.org/showthread.php?t=2083181)

I know this is really more for laptops with switchable graphics, but thought it might at least give me something to work with. Alas!

Oddly, if I switch to a VT, it will appear on my 2 side monitors (those running from the integrated GPU), but nothing I do will get X to run on them. Could I start a second X session and use Xinerama maybe?

---


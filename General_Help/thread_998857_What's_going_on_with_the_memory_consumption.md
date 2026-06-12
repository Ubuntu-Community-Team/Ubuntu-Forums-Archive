---
title: "What's going on with the memory consumption?"
date: 2008-12-01
forum: General Help
---

### Post by siddartha on 2008-12-01
13 years ago, in the days of Windows '95 I was launching an idea (probably not original at all) that once Linux will get the dominant market share and corporate backup it will become worse than Windows.

13 years later, Linux still doesn't have the dominant market share in the desktop, yet it goes worse than Windows and the best argument most can come up with is that it costs nothing as in free beer.

Sure, you can alter the source by yourself, but even programmers prefer the comfort of synaptic and download the precompiled pack. For the most people who can't find an option in 10 tabs the usability people had made just 2 tabs with options. The result is some can't easily set up what they need and the lazy ones for whom this so-called evolution started don't know how to switch to the second tab so they are still limited to just half of the reduced list.

I have been checking up the restults offered by the Gnome System Monitor and nothing else. Still, the results are ugly.

A plain browser with nothing but a blank page is 11M. Open up a single page like slashdot (keep in mind this page is mostly text and it is optimised, unlike most high-traffic web pages). Epiphany goes from 11 to 32,6M and Kazelahaze goes from the same 11 to 39M! And both have banners, and no ad protection.

The compix fusion icon - an icon that sits in the tray and gives you an option to start some configs or choose the windowmanager - 7,9M (!)

Fast user switch applet 4,1M. It has no animation, just reads the user list, the guest session, the shutdown options and if you have something like gaim will show you one closely-related status. A menu for 4M! 15 years ago that was the whole memory of a system and it sure was snappier than the top of the line from today.

GkSudo - it will be there each time you start something like Synaptic which needs root access. 5,7M for doing the same as sudo only with a nice dialog box that throws a shadow over the whole desktop.

Gnome Panel - 10,3M. You would say that JWM doesn't have skins, transparency and all this eye candy. Sure. But the panel plus the whole window manager is 636K (!!!)

Gnome power manager 2,6M. That is needed by all laptops which in most cases means low memory. Also this waste is needed for desktops as well otherwise you will have to wait for a minute before the shutdown menu appears. Maybe this is a bug, still, a 2,6M bug.

Gnome settings daemon - 8,1M just for that.

Gtk window decorator - 7,3M. Remember from above that JWM does the same thing without eye candy and a lot more in 0,6M.

Mixer applet - just to have the unique oportunity to tune up and down the sound costs you 5,1M. And the stupid thing is broken right now as it shows up with the red sign for mute, yet the sound is not muted. Even the menu associated with the mixer doesn't report it as mute. 5,1M wasted for a broken toy just because you don't have the multimedia keys to tune the volume.

Nautilus is 8,8M but it does so many things even in the background it's amaising it works with so little.

For all those pretty applets the only thing you will see it python and some large numbers (over 5M for sure). This python is a nice thing. Better from most angles than java, yet this is no reason to stop at overnight hacks instead of some compiled code.

Speaking of java - the much appreciated azureus torrent client and server was going without counting java over 100M and for about the same functionality and again without counting the Wine server uTorrent does in around 10M. At one point with 250+ torrents in diverse states (downloading, paused, stopped, seeding) it went so high as less than 15M!

Is there any chance of having a distribution examine the insides as well? Ok, the eye candy sells. But is this all that is?

On my laptop I have tried different alternatives to the current options. I have put JWM instead of Gnome. This was just for the argument's sake as I find Windowmaker closer to my liking with its interface and quick response. My reasoning so far was that leads to faster loading times and faster performance.

So getty is 448k unused. ngetty (the only one I could make work without any tweaking) is 8K. Sure it drops the serial line support, but from what I recall most users are finding hard to find a way to do a remote desktop so who bothers about serial lines? Those who do are the ones who should know how to put getty back in ngetty's place.

---

### Post by OrangeCrate on 2008-12-01
See my last post in your other thread.

[http://ubuntuforums.org/showthread.php?t=997932](http://ubuntuforums.org/showthread.php?t=997932)

---

### Post by siddartha on 2008-12-01
Already answered that [http://ubuntuforums.org/showpost.php?p=6287399&postcount=11](http://ubuntuforums.org/showpost.php?p=6287399&postcount=11)

---


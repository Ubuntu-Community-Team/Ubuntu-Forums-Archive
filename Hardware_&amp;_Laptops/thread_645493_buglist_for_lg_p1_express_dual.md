---
title: "buglist for lg p1 express dual"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by stealthc on 2007-12-20
I'm starting to run out of bugs to fix, that I can easily find answers for.... I've done preliminary searches for all that I'm about to list out:

Sound glitches:
the following seems to work best, which I have placed in /etc/modprobe.d/alsa-base
options snd-hda-intel model=xyz
I tried other variants of this setting, lg and auto doesn't work.  With lg I get sound out of my speakers but the headphone jack does not work.
Currently my audio works somewhat fine, though non-functional is the ability to assign various forms of input output to jacks (like I can in windows).  There is no line-out.  I have yet to test line in capabilities (though I suspect that won't work either).  Since switching to this option I have been able to get the internal microphone to work as well.

Things which I will test additionally line in, external mic in.

Audio always starts up at the same volume.  volume up/down buttons don't work when headphones are plugged in (I have to manually change volume using speaker icon on panel)

Bios bug #81 [ 49435000]:
I don't expect to get fixed but it would seem that everybody is still clueless as to what device this would apply to.  Maybe a bios setting?  Anybody got any ideas that says anything more than the nothing I could find on this bug?

Dual head:
it works, but not very well.  When I got the tv output working, I noticed some rather annoying glitches relative to how dual head works in windows.  My laptop screen shows a blue box, and the tv display fills in that blue box with actual video.  When I close my lid to watch a movie because I'd rather not burn a blue box into my screen, it stops displaying the tv out and stops the movie I'm playing.
When I try to use different resolutions, one for the tv-out and one for the laptop's screen, that's when things really begin to get flakey.  It would be nice if I could do anything other than clone my desktop.  It would also be nice if my panel bars wouldn't shrink (and as of yet I have one that doesn't reach acrossed the screen anymore, it's a little short of the edge now.  What I would like for linux to do, would be to clone the output without requiring me to change my desktop resolution.

Panel glitch:
I'm annoyed with the panel bars to the point that I would like to fix their behaviour a little.  There ought to be an edge at the furthest edge of the panel bar relative to the edge of the screen that contains nothing, so when you look at your screen you merely see a little lip that doesn't contain other things (in otherwords, transparent blue is fine which is what I've set mine to).  I would like to perhaps have this lip hidden from view unless I specifically go to that portion of the screen.  It's annoying having my desktop eaten up(even if it's slight) by panel bars which I don't need to use for a while.

PCMCIA:
There is no indication of devices being plugged into or removed from pcmcia card slot?

Any thoughts or suggestions?

I've still gotta test the memory card reader (though that isn't the most important thing on my list), I'm annoyed how I have other buttons (direct media, srs) which don't work (not to mention fn+function keys, only sleep, mute and brightness up/down work).

Further untestest components include: 1394, vga out, lan and modem.

I've also found the wireless network connection icon on the panel to be fairly sluggish and am considering using kismet, though I think I might need a new network card for that since once I get into the wireless stuff this intel card stinks and lacks features and functions.  I was wanting to grab most of the applications found in backtrack 3, since I'm not fond of their distro and this seems to be a better, more useful version of linux I'd rather stick with ubuntu.

Any help would be appreciated.

---


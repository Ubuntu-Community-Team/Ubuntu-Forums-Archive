---
title: "Tricky Problem: X broken on a modded Dell SC420"
date: 2005-12-01
forum: General Help
---

### Post by LodeRunner on 2005-12-01
My appologies if this would be better suited for an x.org forum.  Ubuntu's been working out so well on my laptop that I decided to try it on my desktop as well.  This is what I get trying to boot after a fresh default install:

> Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o"
No Symbols found
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o"
No Symbols found
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o"
No Symbols found
(EE) No devices detected

Fatal server error:
no screens found

It's a Dell SC420 with the 2.8Ghz P4 with HT.  Windows is installed on the SATA drive; Ubuntu was installed on the PATA drive.  

I am *not* using onboard video.  I performed a motherboard mod allowing the insertion of a 16x PCI-Express video card (a Radeon x800XL) into the 8x slot.  This is a fairly well known mod, and I've had absolutely no problems with the card in XP (or Knoppix 4.0.)  However, I think this is the most likely culprit.  

The detailed report shows:

> 
(II) ATI: Candidate "Device" section "ATI Technologies, Inc. Radeon x800 XL (R430 UM)".
(WW)ATI: PCI Mach64 in slot 1:0:0 could not be detected!
(WW)ATI: PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.

Fatal Server error:

no screens found

 
I could probably fix it by taking out the Radeon, but that isn't an acceptable long term solution.  I actually paid more for that thing than I did the SC420 itself, and I use it regularly to game (under XP.)

The problem probably has to do with the fact that it's a (pseudo) 8x PCI-Express slot.  It's the size of a regular 16x slot, but it has 8x pins (and a plastic divider to prevent the insertion of 16x-sized cards.) This, as it turns out, is not a problem for the current batch of 16x PCI-Express video cards.  The interface is not the bottleneck--theoretically even 4x would be more than fast enough.  Some creative and very brave dude hacked off the little plastic divider, stuck in a 16x PCI-E video card, and lo and behold it just worked, *even though many of the pins on the card were resting on bare plastic.*  Those pins aren't necessary for the x800XL to function or even achieve maximum performance, but I'm thinking maybe x.org uses them when it tries to probe the card.

So, assuming this is indeed the source of the problem, is there any way to tell X.org "screw it, just believe me, it's an x800XL, now use it!!" ?

---

### Post by akiro.yamamoto on 2005-12-01
I'm not sure if this will help but try:
CODE:
sudo dexconf
See if that can create a new xorg.conf file for you untill you can install the ATI drivers for your card.
Regards

---


---
title: "2 PC'S + 2 OS's = messed-up Xorg on one day ???"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by perixx on 2007-10-16
Can anybody make sense out of this:


I got 2 different PC's with 
Xubuntu 7.04 (old PC with ATI Rage 128 Pro CL PF AGP) 
and 
Puppy 2.15 (new PC with an ATI X1950GT type card) 
- physically separated from each other...


Yesterday evening, the one with Xubuntu would start the 'Xubuntu' splash screen (graphically OK) and then suddenly breaking off the boot sequence, showing for a second or so a text-based login and then switching to a red / grey /blue error message (text): X Window System Version 7.2.0 

(I suppose the same content as /var/log/xorg.0.log) - some lines excerpted today - AFTER I made DPKG-RECONFIGURE, so it might not match with the one yesterday evening:

....
(EE) unable to find a valid framebuffer device
(EE) R128(0): failed to open framebuffer device, consult warnings ...
(EE) Screen(s) found, but none have a usable configuration

Fatal server error: no screens found.
.
.
(II) Setting vga for screen0:
(II) R128(0): PCI bus 1 card 0 func 0
(**) R128(0): Depth 16 = 16 bits stored in 2 bytes....
.
.
(**) R128(0): Option "UseFBDev" "true"
(II) loading sub module "vgahw"
.
.     
Ati driver version 6.6.3 -Y submodule "r128"
.
.

(WW) open /dev/fb0: No such file or directory
.
.
.
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
.
.

There's also a (WW) warning, that /usr/share/fons/X11/cyryllic doesn't exist, and that the entry's being deleted from path


I cannot remember having specified the cyryllic alphabet at all. 

Unfortunately, I hadn't made a backup of xorg.conf by now, so I couldn't just switch back. I wasn't able to make sense out of the 'new' xorg.conf... maybe I were just too tired :]

After getting nowhere, I startet looking for an answer here with the Puppy-PC (where I encountered a similar problem first, which I could circumvent by using 'xorgwizard' and changing to 'vesa' driver).... but didn't find an answer but the

sudo dpkg-reconfigure -phigh xorg-server 

command, which I used then. After a long trial of setting up everything newly - no success, still the same error at boot-up. 

Today, I managed  to find out that - apparently - the vertical refresh rate was set too high. I can remember setting this one to 150 Hz, because I've read in some user's description the monitor was good for a range of 30-91H / 50-150V, but do not remember setting it yesterday. 
In fact, I've still been using the Xubuntu machine yesterday afternoon and had the problems in the evening, when switching it on again unsuspiciously... 


While looking a little closer to the xorg.0.log, I noticed, that the 'framebuffer' option might be the culprit (I've activated this one while doing dpkg-reconfigure yesterday), but cannot remember where I could've set it BEFORE, in any way whatsoever.

Actually, while doing some intense trial-and-error editing the xorg.conf and rebooting again, I found out, that not setting the monitor-default to 16bit color depth caused the Xorg-server problem, nor the high refresh rates of 92H/150V... the ONLY thing that produced the same error window at bootup was changing the 'framebuffer' option to 'true' - which I really don't know how it could happen 'by itself' in the first place, even less, how I should've been doing so...


Overall:

both PC's up and running again, though I got not the faintest idea what was causing this mess....   

While speaking of it... I really don't understand why there's no such simply thing like 'xorgwizard' under Puppy here for the Ubuntu bash, sparing user's reconfiguring EVERYTHING new, instead of just resetting what's needed (the video in this case).


regards,

perixx

---


---
title: "Geforce2 Ti and MX400 difference"
date: 2008-08-29
forum: General Help
---

### Post by Whydoe on 2008-08-29
I just spent a week setting up my sons computer to multiboot 3 different OS's. (XP/98/Hardy-Ubuntu).  I have a Geforce2 Ti card, he has a Geforce2 MX400 card.  For some reason, I'm forced to use a legacy driver making desktop effects unavailable, and he gets the non-legacy driver (glx).  I tried to remove my legacy driver and try to install the glx version, but it didn't seem to go anywhere.  I thought the Ti card was better than the MX400.  Not a big deal, everything works fine other than desktop effects.  I can still play all the games.  
Do I need to completely remove all nvidia drivers, settings, etc and then install glx drivers (not the newest ones obviously)?  When I go to my hardware drivers settings, it only gives me the legacy driver option - even after I remove them using package manager.

---

### Post by overdrank on 2008-08-30
Hi and as I understood it the MX400 was a little newer than the Geforce 2. But what do I know :) Do both cards have the same amount of memory? You may try and remove the nvidia drivers from the Geforce card and then try Envy to install the drivers.

---

### Post by Whydoe on 2008-08-30
Yep.  Tried that.  It is a Geforce2 MX400 and according to nvidia, the Ti version is far superior to the MX400 version.  I'm just going through the HOW TO Install Nvidia driver Hardy 8.04 forum page.  I think I need a fresh install of everything nvidia, including the nvidia kernel, config, settings, etc.  If I just remove legacy driver from Synaptic Package Manager, it is still left as my only option when I go to set my nvidia driver in Hardware Manager ie. legacy.

---

### Post by Whydoe on 2008-08-30
Ok, this might be confusing or helpful.  Since I cloned my linux partition onto my sons computer, I am setup as admin on his computer (obviously), and I have my son as an additional user.  If I log in under my sons user name, I have desktop effects enabled.  Under my name, they are off, and I can't turn them on.  What the heck happened there?  And no legacy drivers either.  How is that possible if it's an exact clone of my partition with legacy drivers?

---

### Post by Whydoe on 2008-08-30
Ok.  I give up.  I've uninstalled ALL nvidia based references in package manager.  Installed the NVIDIA driver - from the nvidia web site. NVIDIA-Linux-x86-71.86.06-pkg1.run  Restarted.  Works fine - but still not able to add ANY desktop effects.  I even installed another user to test out if maybe that would help.  Nope.  Maybe I'm just being picky, and really, it's not a big deal.  It just doesn't make sense.  I've also re-installed the glx driver after I installed the one from the nvidia web page.  The didn't work.  Reinstalled the other one... and it's back to normal.   Although, now I have neither glx or legacy drivers showing up in my Hardware Drivers.  I guess it's going to suck once I have to upgrade isn't it?

---

### Post by edwardp on 2008-08-30
I had some issues with my GeForce2 MX 400 card, this was with a different distro, but I am currently in the middle of installing xubuntu (for the first time!) on another desktop (below).

I changed the x.org server to use the x.org "vesa" driver with the GeForce card, I found that it resulted in X using less memory than it had before.  Since I am not a gamer and do not use a 3D desktop, I found that this setting worked perfectly.

---

### Post by Whydoe on 2008-08-30
Ya.  I'm being picky.  It's using the "vesa" driver on mine too.  That may be why.  All the games work though.  I'm sure I'll figure it out sometime.  I'm surprised with all the tweeking and driver installs-uninstalls I've done I haven't completely messed my system up.  If it was Windows, it would've crapped out a while ago.

---

### Post by jrusso2 on 2008-08-30
I have the Geforce2 MX400 here and always had to use the legacy nvidia driver.  Desktop effects worked on feisty but never got it working on Gutsy though.

---

### Post by Whydoe on 2008-08-30
Have you tried Hardy yet?  MX400 is setup using non-legacy driver on my sons.  Don't ask me how it picked it up.  Maybe it has to do something with the motherboard chip set.  VIA isn't the best when it comes to compatibility I've heard.  Which is what is in my computer.

---


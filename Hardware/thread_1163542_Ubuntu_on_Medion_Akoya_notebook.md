---
title: "Ubuntu on Medion Akoya notebook?"
date: 2009-05-18
forum: Hardware
---

### Post by grimo1re on 2009-05-18
Hi,
 
I'm a complete Linux beginner (as in have seen it once, never actually used it before) and am looking for some advice. I've just bought a Medion Akoya S2211 notebook (MD 97560) from the Aldi and was hoping to try an Ubuntu flavour. After doing a a bit of a Google search and a search on this forum, it doesn't look like this will 'just work'. I'm especially worried about the wireless thingy not working under linux.
 
Am I wrong? Will I have to do 'scary' linux things if I do try to install Ubuntu on the notebook or should I stay with Windows Vista?
 
I was going to use the notebook for word processing, web surfing, e-mail, watching some videos, working via web. Nothing strenous really...
 
Thanks for any advice you guys can give me.
 
Cheers,
 
grim

---

### Post by andre_orwell on 2011-12-14
Well this is obviously not very timely for you but I thought it might be worth posting anyway just as this post shows up as one of the only that ties this particular laptop and ubuntu together.

I've run ubuntu on this laptop from the day I bought it.  The hardware support is ok but not automatic.  There are some tweaks required but after these are applied it works flawlessly (as flawless as software is in general).  

I'm now running 11.10. Here are the problems and fixes:

P: Wireless networking fails after suspend-resume
S: problem is with power management.  To fix (see [http://ubuntuforums.org/showthread.php?t=1751094):](http://ubuntuforums.org/showthread.php?t=1751094):)
sudo touch /etc/pm/power.d/wireless
sudo touch /etc/pm/power.d/pcie_aspm

P: no sound when headphone socket in use
S: This one is *hard* to find a fix for but the fix is simple in the end:
edit /etc/modprobe.d/alsa-base.conf and append the lines
options snd-hda-intel model=generic
options snd-hda-intel enable_msi=1

then enjoy.

---

### Post by overdrank on 2011-12-14
Back to sleep thread. Thread closed.

---


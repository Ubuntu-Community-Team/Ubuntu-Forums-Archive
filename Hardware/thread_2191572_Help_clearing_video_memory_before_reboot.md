---
title: "Help clearing video memory before reboot"
date: 2013-12-03
forum: Hardware
---

### Post by Genera1080 on 2013-12-03
Has anyone got any ideas what's going on? - sometimes when logging into Ubuntu/Lubuntu (at the login screen), the background of the login screen shows tiled screenshots of the last part of the previous session I had on other distros (Lubuntu/Mint/Gentoo,Manjaro whatever) - for example, suppose I'm in Manjaro, finishing off looking at YouTube on Firefox - when I log out of Manjaro and reboot into Ubuntu, the Ubuntu login screen contains a garbled/tiled screenshot of the last YouTube bits I was looking at on Manjaro - is this some kind of GPU or Bios malware constantly taking screenshots that somehow floats over (unexpectedly, from the Malware's POV) to a new session or distro?? - anyone got any hunches or ideas what this could be? - cheers, thanks for any help.

---

### Post by The Cog on 2013-12-03
Sounds like you have video driver issues, and the previous desktop is still there in the graphics card's memory somewhere. I've seen that just once on this 'puter here. It feels spooky. (I *presume* this effect is only from reboot, and not from a cold power-on.)

---

### Post by Genera1080 on 2013-12-03
Hi Cog, yes, it only happens sometimes on a reboot - never on a cold boot - (if I get the garbled/tiled screenshot login screen, I just reboot immeadiately and the next login screen is back to normal) - regards the graphics card, its a cheap budget MSI Nvidia 210 1GB (my previous Radeon 6770 shorted out) so I'm on a budget hold-over card at the moment - interestingly, regards graphics glitches, I often notice a small block of red pixels on the screen when booting up any distro (these pixels do sort of feel like a graphic-glitch, so they might fit in with the above).

---

### Post by tgalati4 on 2013-12-03
I've seen it as well over the years with various graphics cards.  It's harmless, but can be annoying if you share the computer with others. You would need to run a shutdown script that wipes the graphics memory just before shutdown--and it would vary with each graphics card, since the desktop environment is obviously not doing it.

I would change the title of the post to reflect this behavior and then "Report Post" to ask a moderator to change it to the hardware forum.

---

### Post by Genera1080 on 2013-12-03
Thanks guys - yes, feel free to move the thread Cog - hardware, D.E etc - cheers

---

### Post by CharlesA on 2013-12-03
Title changed and moved to hardware. I've seen this too, like tgalati4, but the majority of the stuff I found with a quick search was related to Apple products.

What video drivers are you using? I don't think that's the problem, but it might be helpful to know.

---

### Post by Genera1080 on 2013-12-03
Just the standard X drivers - I've haven't chose any specific Nvidia or AMD drivers recently (I used to do that a couple of years ago, but have been happy on the generic ones lately) - on another thread I mentioned this strange graphic appearing on the GRUB 2 menu when using no graphics card, (just the motherboard on-board graphics) - there's a screenshot on the thread below which shows the ''graphic'' on my GRUB 2 menu screen (it appears when using the MB's on-board graphics adapted only - it doesnt appear when using a standalone graphics card)

[http://ubuntuforums.org/showthread.php?t=2187407](http://ubuntuforums.org/showthread.php?t=2187407)

 [http://ubuntuforums.org/attachment.php?attachmentid=247782&d=1384237687](http://ubuntuforums.org/attachment.php?attachmentid=247782&d=1384237687)

I was wondering at the time whether I had any BIOS Malware (because something was obviously loading up (quite explicitly) - or possibly a driver for the motherboard's on-board graphics? - it seemed strange, all the same though - don't remember seeing anything like that over the last 10 years in Linux - never found an answer to what it could be.

---


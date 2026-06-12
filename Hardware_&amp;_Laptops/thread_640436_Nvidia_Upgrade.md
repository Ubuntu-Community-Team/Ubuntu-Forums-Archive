---
title: "Nvidia Upgrade"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by Menthol on 2007-12-14
I'll be upgrading an old Nvidia card to the newer GeForce 7600 GT 256MB soon. I was wondering if there were any settings I might have to change manually in Ubuntu I dont know about, to make it utilise the full card.
I dont want to install the card, only to have the settings stuck on 128MB for the card because Ubuntu has stored the settings for the old card.

So in a nutshell, does anyone know of any settings I'll need to change manually in Linux?

---

### Post by frodon on 2007-12-14
It is not working like that, new hardware will be detected on boot so it won't use old settings.
However you may want to reconfigure you xorg.conf especially if you tweaked it, if you didn't maybe you can skip this step.

Then if you need to install the nvidia drivers use the restricted driver manager.

---

### Post by Menthol on 2007-12-14
Many thanks, Will do that :-)

---

### Post by oneiota on 2007-12-14
I have been enjoying a well-running Gutsy installation and just upgraded the graphics card to a GeForce7600GT 256MB PCI-E and I now get errors now when I try to boot.  

It certainly won't run the X server unless I remove the card and put the old one back in.  (I have installed the Nvidia drivers manually but that hasn't made the difference.)

I don't think this issue is the new card as I've tried booting into Windows (same machine) with the new card and it works very well.  

From what I've read, I don't know that my problem is typical, but you may not find a graphics card upgrade working as straightforwardly as expected.

---

### Post by Menthol on 2007-12-14
Interesting, thanks for the warning.  I want to avoid a reinstall if at all possible but if its needed its needed.  I'll just have to cross my fingers and hope for the best I guess.

---

### Post by oneiota on 2007-12-22
Hi there,

Just  a note that I had to give up and reinstall.  That worked well but I do wish I could have done it without as I'm having DVD issues now.  Though, I do tell myself that I learn more each time I reinstall! :)

---


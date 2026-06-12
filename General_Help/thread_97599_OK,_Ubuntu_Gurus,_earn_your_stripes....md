---
title: "OK, Ubuntu Gurus, earn your stripes..."
date: 2005-12-01
forum: General Help
---

### Post by tman_ubuntu on 2005-12-01
:p 

Pleeeeeezzzze heeeelp!  I have an AMD 900 Duron with a 32MB Nvidia card that has a Riva TNT2 chipset.  The problem is that Gnome locks up at the logon screen.  At startup, I get the nvidia logo screen, then it gets to the GDM and freezes with the busy cursor showing (a brown blank screen with busy cursor).  At that point I have to restart.  I have loaded the restricted-legacy versions of the nvidia drivers.  I'd like to think that I have pretty good experience with these drivers however this one has me stumped.  I've tried to enable and disable options (dri, vbe, glx, etc...) nothing seem to work.  The only time I can get X and Gnome working is if I change the "nvidia" back to "nv".

Pleee hee heeeez help.  My kids will love you for it.  Thanks in advance. :D

---

### Post by atoponce on 2005-12-01
What are the specs of your system?  nVidia and ATi drivers are tough to work with in Linux.  Your best bet is probably to switch to a more generic driver like the 'vesa' driver.  Although 3d rendering will most likely be disabled, I don't think you are too concerned about that, are you?

---

### Post by tman_ubuntu on 2005-12-01
[QUOTE=atoponce]What are the specs of your system?  nVidia and ATi drivers are tough to work with in Linux.  Your best bet is probably to switch to a more generic driver like the 'vesa' driver.  Although 3d rendering will most likely be disabled, I don't think you are too concerned about that, are you?[/QUOTE]

I had this same card in an old pc (AMD K6-2 450) and it worked fine with ubuntu and the legacy drivers (only problem with K6 450 is that the cpu overheated after about an half an hour).  I would like to get this working to take some of the video work load from the CPU since it's only a 900Mhz Duron.  

I'm thinking my problem is that the legacy drivers don't work with the AMD K7 CPU that the Riva TNT2 card requires.  I've tried to use the non legacy version of the nvidia drivers and it simply won't start the X server period.  Anyways my specs:

ECS K7SEM motherboard
AMD 900Mhz Duron
512Mb SDRAMM
32Mb nVidia Riva TNT2 video card
Integrated sound
Onboard LAN

---

### Post by tman_ubuntu on 2005-12-01
Bumpity... :D

---


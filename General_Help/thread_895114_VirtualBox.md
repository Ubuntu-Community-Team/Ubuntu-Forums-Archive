---
title: "VirtualBox"
date: 2008-08-19
forum: General Help
---

### Post by FLCL on 2008-08-19
Does anyone have any idea how to un-maximize the damn thing? 
Cntrl+f maximizes it, so you'd assume you'd be able to toggle it with the same key sequence;BUT i guess not -_-**

Anyone got any idea?:mad:

---

### Post by wd5gnr on 2008-08-19
If you haven't changed anything, press the RIGHT HAND Control key and F. You can also get a menu with Right Control Home.

---

### Post by wenuswilson on 2008-08-19
(Experimenting on my VBox -- it maximized fine and when when I R-CRTL + f again it logged out of my Ubuntu session.)

Otherwise, it should toggle.
My problem with VBox is that I can't get a shared folder with the guest additions thing. It messes up my the display settings and forces me to crlt+alt+backspace to reset.

[[Don't intend to steal the thread, just curious on VBox issues]]

---

### Post by FLCL on 2008-08-19
Ah, thank you. Thats the only sequence i didn't try x.x;

And it's fine to seek other help in this thread, i don't mind.

---

### Post by Mgiacchetti on 2008-08-19
> **wenuswilson said:**
> (Experimenting on my VBox -- it maximized fine and when when I R-CRTL + f again it logged out of my Ubuntu session.)

Otherwise, it should toggle.
My problem with VBox is that I can't get a shared folder with the guest additions thing. It messes up my the display settings and forces me to crlt+alt+backspace to reset.

[[Don't intend to steal the thread, just curious on VBox issues]]
XP in virtualbox??
Is it ose? if not its probably the bad virtual box guest additions. 1.6.2-1.6.4??

download the iso from [here]("http://www.virtualbox.de/download/1.6.0/") should solve your problem.

UNINSTALL GUEST ADDITIONS IN YOUR GUEST OS BEFORE INSTALLING THIS VERSION


If its ose, ditch it and go [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") get your distro's install, then go [here]("http://www.virtualbox.de/download/1.6.0/") and downgrade your Guest additions as noted above.

---

### Post by wenuswilson on 2008-08-21
> **Mgiacchetti said:**
> XP in virtualbox??
Is it ose? if not its probably the bad virtual box guest additions. 1.6.2-1.6.4??

download the iso from [here]("http://www.virtualbox.de/download/1.6.0/") should solve your problem.

UNINSTALL GUEST ADDITIONS IN YOUR GUEST OS BEFORE INSTALLING THIS VERSION


If its ose, ditch it and go [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") get your distro's install, then go [here]("http://www.virtualbox.de/download/1.6.0/") and downgrade your Guest additions as noted above.

I installed 1.6 from the link and it worked beautifully, I do have OSE but it still worked.. When I clicked the "Install Guest Additions..." under devices it gives me 1.5.9 perhaps that's screwy too. Either way, no problems. Thanks.

---


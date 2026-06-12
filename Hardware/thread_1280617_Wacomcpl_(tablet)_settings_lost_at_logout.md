---
title: "Wacomcpl (tablet) settings lost at logout"
date: 2009-10-02
forum: Hardware
---

### Post by Mercredi on 2009-10-02
I'm using wacomcpl to change my tablet settings, including screen mapping. However, these changes are lost after logging out and logging back in. I've tried gksudo'ing wacomcpl, but that doesn't make the changes "stick".  Furthermore,Ubuntu doesn't always recognize that the tablet exists after waking up from hibernation; I have to unplug and reconnect the tablet.

Can anyone either suggest what to do so the changes made with wacomcpl stick, or point me in the direction of a guide that will tell me what changes to make to my xorg.conf? 
(The Linux Wacom project page tells me how to put the basic information about the tablet's existence in xorg.conf, but not how to change screen mapping and toolbutton settings there.)

---

### Post by Favux on 2009-10-02
Hi Mercredi,

What version of Ubuntu are you using?  Which Wacom tablet do you have?

To get the .xinitrc file (a hidden file) that wacomcpl generates to apply through a log out see "Section 3: Calibrating your Tablet" here:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

---

### Post by Mercredi on 2009-10-02
Ah, whoops, yes, that would be important information. I'm using an ancient Graphire on Jaunty.

I'll take a look at your link as soon as I can get the tablet working again at all - I installed a new graphics card, and I'm still correcting the damage that did to all my settings (including recognising the tablet at all.)

EDIT: Thank you, following the instructions you linked resolved the issue. I confess I had been a bit skeptical because it was on the thread for Tablet PCs (and not graphics tablets), but it worked.

---


---
title: "Should I install Nvidia drivers?"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by Navin_Johnson on 2005-06-23
Hello,

Back with Linux again after a year hiatus.  Really liking Ubuntu (the forum has been very helpful) and I've got everything just about set up to my liking.

Now I'm trying to decide whether I ought to install the Nvidia drivers for my integrated 3d card.  I don't play games anymore :sad:  (3 kids, full time job, house and graduate school doesn't leave time).  Mainly use the computer for OpenOffice apps (esp writer), web browsing, email, dvd backups.  

The only reason I hesitate to do the Nvidia drivers is the headache it caused last time (a year ago on Fedora).  I got it working but what a pain.  Based on my computer usage is there any reason I should install them now?  Are the drivers any better than they were a year ago?

Thank you in advance for any replies.
Navin_Johnson (Eric)

---

### Post by bunced on 2005-06-23
Short answer YES,

They are much easier in Fedora - just install nvida-glx from Synaptic, modprobe nvidia and change the device section of /etc/X11/xorg.conf

Regards
David

---

### Post by astoltz on 2005-06-23
If you haven't already found it, Ubuntuguide has a pretty good Howto for installing the nVidia drivers. [Check it out.](http://ubuntuguide.org/#installnvidiadriver)

Oh yeah, ther have been many reports of system crashes with the nVidia drivers **AND** the RenderAccel option turned on.  Without the RenderAccel option, the nVidia driver seems to behave.

---

### Post by Navin_Johnson on 2005-06-24
Thanks for the advice.  I went ahead and installed and it went without a hitch.  Seems to be stable too, which was really my main concern.

Navin Johnson (Eric)

---


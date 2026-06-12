---
title: "Configure Synaptic touchpad, losing desktop"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by hhh on 2005-12-21
Sorry to crosspost, I'm getting no response in the Beginner forum...
[http://ubuntuforums.org/showthread.php?t=106803](http://ubuntuforums.org/showthread.php?t=106803)

---

### Post by Lambert on 2005-12-21
Gentoo wiki looks to have some good information on synaptic touchpad. see if any of this helps you.

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

---

### Post by hhh on 2005-12-22
Thanks Lambert, I have that link. I've been getting stuck right at the beginning with emerging the driver, I think. Is this a good link for that?...
[http://linuxreviews.org/gentoo/emerge/](http://linuxreviews.org/gentoo/emerge/)
Then when I edit the xorg file and reboot I lose my desktop. Now I've got desktop icons that I can't left click on to open, my wireless connection has disappeared and my touchpad makes surfing an exercise in frustration.

Looks like I'll be reinstalling the OS and starting from scratch. Hopefully ndiswrapper won't take 20 hours to configure this time.

---

### Post by Lambert on 2005-12-22
sorry should have posted a little more info. The link is for gentoo which has differences from ubuntu. The guide should not be followed but the settings in xorg.conf to give you the options you can play with to set up your touch pad.

Where they say emerge the driver, that's their method of installing the driver. For ubuntu you can use apt-get or the synaptic graphical package manager (system>administration>its_in_this_list) to install from ubuntu repositories. You need to install this package I believe.

[http://packages.ubuntu.com/breezy/x11/xorg-driver-synaptics](http://packages.ubuntu.com/breezy/x11/xorg-driver-synaptics)

---

### Post by hhh on 2005-12-22
Thanks for that reply and link, Lambert. I also discovered that I had enabled extra repositories incorrectly (had Hoary enabled instead of Breezy), so I was getting all sorts of errors.

Where it stands now is I've wiped the laptop clean and done a fresh Breezy install and have added the correct repositories...
[http://www.psychocats.net/linux/](http://www.psychocats.net/linux/)

No turning back now, I've got a ton of reading to do now, a crash course in Ubuntu. I'm confident I'll look back in six months and realize migrating to LInux was the best computer decision I ever made.

---

### Post by Lambert on 2005-12-22
>  I'm confident I'll look back in six months and realize migrating to LInux was the best computer decision I ever made.

That's exactly where I'm at today.:D

---


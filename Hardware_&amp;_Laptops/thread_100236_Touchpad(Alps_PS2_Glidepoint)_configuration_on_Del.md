---
title: "Touchpad(Alps PS/2 Glidepoint) configuration on Dell D505 with Ubuntu 5.10 (Breezy)"
date: 2005-12-07
forum: Hardware &amp; Laptops
---

### Post by erlingre on 2005-12-07
Hello,

I have recently started in a new job which involves maintaining among other things 60-70 Dell D505 Laptops with Ubuntu 5.10.

My users are complaining about the touchpad which they tap and doubletap accidentally while for instance processing text in OpenOffice or using Mozilla Firefox.
I have tried the various solutions described in other threads here and from other sources, but have not sucessfully been able to disable touchpad tapping so far.

The Dells have ALPS PS/2 Glidepoint touchpads. According to the documentation
in /usr/share/doc/xorg-driver-synaptics I may have to patch the kernel in order to disable touchpad tapping. I have tried to apply the patch in the README.alps file but get 1 out of 2 hunks failed (typing "gunzip -c patchfile.gz | patch -p1"). Parts of the patch seems to be applied correctly so I think the command line is correct.

Have anyone a suggestion for how to solve this problem? preferably quick and simple as I have a lot of other things to do.

Thanks in advance,

Erling

---

### Post by WebDrake on 2005-12-07
I also have a Dell with an ALPS touchpad and encountered similar problems in terms of it being over-sensitive.

This forum posting explains how to fix it---in any case it worked for me:

[http://ubuntuforums.org/showthread.php?t=78904](http://ubuntuforums.org/showthread.php?t=78904)

Following use of that method, I now have proper touchpad scrolling, I no longer get the problem of the touchpad accidentally picking up a "tap" as you describe, but I can still *deliberately* tap when I want to.  But maybe you already tried that method and it's not good enough for your requirements... :rolleyes:

---


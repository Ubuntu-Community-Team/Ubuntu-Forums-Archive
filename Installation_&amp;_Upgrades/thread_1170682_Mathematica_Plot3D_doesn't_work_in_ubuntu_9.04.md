---
title: "Mathematica Plot3D doesn't work in ubuntu 9.04"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by andres.ordonez on 2009-05-26
Hi, I have an AcerAspire 5735-4950 and after upgrading to 9.04 from 8.10 Plot3D doesn't display the plot. The plot is displayed only when rotating it.

(I'm taking the multivariable calculus course and this is the most important feature for me right now).

Please help.

---

### Post by Mark Phelps on 2009-05-27
This is why LiveCDs are made available -- to try out a new release BEFORE upgrading your machine.

And, don't ask about rollback to 8.10 because there's no simple solution.

Your best recourse, unless someone jumps in with a ready answer, would be to contact the folks you bought this from and see what they suggest.

---

### Post by dmonkey on 2009-05-29
Try to use the UXA feature of the new graphics drivers in Ubuntu. To do this, edit the xorg.conf (normally located at /etc/X11/xorg.conf) in the "Device" section:

Section "Device"
	Identifier	"Configured Video Device"
	Option 		"AccelMethod" "uxa"
EndSection

This works for me. And yes, things can seem like a bad idea in hindsight, but I think lecturing is also not very useful...

---

### Post by andres.ordonez on 2009-06-15
Thanks dmonkey! that worked

---

### Post by ythaaa on 2009-07-07
hi,

the solution works for me. in kubuntu 9.04. however after i change the accelmethod, my graphics very slow. changing desktop becomes slow. changing back to previous setting then everything is fine. my setting is

Section "Device"
        Identifier      "Configured Video Device"
        Option         "AccelMethod" "uxa"
        Option         "UseFBDev"              "true"
EndSection

i also tried the solution in [http://ubuntuforums.org/showthread.php?t=610872](http://ubuntuforums.org/showthread.php?t=610872)  it also works, but putting the option -mesa -defaulvisual    will cause me a problem. that is, when i rotate the plot, it takes quite some time to regenerate a new plot. without the option, rotating the image is fine and fast for me. 

will appreciate any help from anyone.... thank you in advance...

---


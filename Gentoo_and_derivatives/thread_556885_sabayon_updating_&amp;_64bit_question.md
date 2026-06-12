---
title: "sabayon: updating &amp; 64bit question"
date: 2007-09-21
forum: Gentoo and derivatives
---

### Post by dracule on 2007-09-21
Hey, i installed sabayon 64 bit 3.4e and loved it from the get go. 

but it runs A LOT hotter than my other distros and uses an extreme ammount of ram (600+ on a 1 gb sys on a cold boot)

also it uses 160+ processes.


so my question is if i switch from 64bit to 32bit if less ram would be used, and maybe it would run cooler? i mean it is ridiculous when i boot into sabayon, my fan runs full throttle non-stop, non of my other distros ever did this (even with compiz and stuff)

also, how do you fricken update the damn thing?

---

### Post by rsambuca on 2007-09-21
To update:

emerge --sync

then 

emerge -uDNav world

(these are gentoo methods, but I assume they are the same)

---

### Post by dracule on 2007-09-22
> **rsambuca said:**
> To update:

emerge --sync

then 

emerge -uDNav world

(these are gentoo methods, but I assume they are the same)

no, i get a crap load of errors, and it asks me to remove tons of packages that way.

---

### Post by mips on 2007-09-22
> **rsambuca said:**
> 
emerge -uDNav world


I don't think that is recommended for Sabayon.

---

### Post by rsambuca on 2007-09-22
Yeah, sorry about that.  I just noticed it on the Sabayon wiki.  There is a [guide to updating on Sabayon]("http://wiki.sabayonlinux.org/index.php?title=Unoffical_Guide_To_World_Update").  Perhaps you should try looking at the docs once in a while ;)

---

### Post by dracule on 2007-09-23
> **rsambuca said:**
> Yeah, sorry about that.  I just noticed it on the Sabayon wiki.  There is a [guide to updating on Sabayon]("http://wiki.sabayonlinux.org/index.php?title=Unoffical_Guide_To_World_Update").  Perhaps you should try looking at the docs once in a while ;)

actually i saw that, and was hoping that there would be an easier way other than spending like 2 hours coniguring the damn thing. i just installed ubuntu. sabayon needs a better package manager. i wish there was a sabayon like thing for ubuntu,

like all the latest packages on a ubuntu base.

---

### Post by Frak on 2007-09-24
Actually portage is a great package manager as long as you don't mind breakage amoung uninstalling (no dependency checking), long waits, and alot of HD space being used.

Benefit, a fraction better speed.

Me, I use Fink on OS X, which is a port of Ports. Portage is also a port of Ports. Closest thing I have.

---

### Post by cepal on 2009-02-04
1) regarding Sabayon: 
- I just tested 4.0 R1 for a while and just gave up. While consuming hell of a disk space, I didn't see any improvement, well maybe a better memory management, but I bet this can be achieved in Ubuntu as well by stopping unused services and maybe a little tweaking of Gnome, Firefox etc.
- while Ubuntu had no problems in taking over my old home inherited frome being used in Fedora, Sabayon totally screwed my Gnome settings; now back in Ubuntu, but having not properly backed up my home, it's screwed anyway, at least it works and I will just have to install and apply some nice themese etc...
- one BIG plus for Sabayon: combination of equo/entropy (binary repositories) and emerge/portage for sources (if I don't get it wrong) inherited from Gentoo... 
- another yet BIGGER plus: they still use ALSA, grrrreat!!! Who the f**k needs Pulse Audio and similar sh*t? I don't want a streaming server, I want my lappy to work smotthly, fuel-economically (making run on batteries as long as possible) (btw, ever heard of "powertop"?) and flawlessly, without breakdowns etc... (which Ubuntu does, actually)

But the Sabayon team did a good piece of work and I believe version 5 will be something really cool, unless they'd keep it on bleeding stability level... So I moved back to UBUNTU :-). Originally I was using Fedora, but the version upgrades were damn painful and last bit was when after upgrading to F10 the x weren't running on dual view (on Intel card)... They say it's fixed now, but I am no more interested :-), although I still keep the small partition with Fedora on my system as a backup if Ubuntu goes to hell...

CePal

---


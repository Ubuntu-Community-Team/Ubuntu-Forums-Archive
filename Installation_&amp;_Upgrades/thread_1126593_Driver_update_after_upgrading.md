---
title: "Driver update after upgrading"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by dsnettleton on 2009-04-15
I upgraded to the Jaunty Jackalope (apparently) somewhat prematurely.  I probably should have waited until the beta was over, but I'm new at this.  Anyways, most everything still runs pretty well, but my Compiz is not among those things.  One of the reasons I was attracted to the upgrade was its prettier interface (notifications, etc).  This became somewhat self-defeating with compiz gone, however.  I ran compiz check and got this little spiel:


> Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82865G Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use

I interpret this to indicate that the driver for my graphics card is not compatible with the upgrade,  So I have a two-part question.  Firstly, how long a wait should I expect until the driver catch up with the OS.  Secondly, is there any convenient way I can "roll back" the update that won't erase my regular system settings?

I suppose it's a three-part question now, but does this happen often when ubuntu is upgraded?

Thanks,
--D. Scott Nettleton

---


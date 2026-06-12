---
title: "Compiz Fusion doesn't work in Ubuntu 8.10 with Intel 82946GZ/GL"
date: 2008-11-10
forum: General Help
---

### Post by Magic_Spehar on 2008-11-10
When I put "visual effects" from "none" to "normal" or "extra" it says "desktop effects could not be enabled".  I have an Intel 82946GZ/GL as graphical card. 

I already tried "gksudo displayconfig-gtk" and then changed my graphics card to "Intel experimental modesetting driver" but I didn't have any luck with that.

I also tried "compiz check" and it said: 

"Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems.../usr/bin/compiz-check: line 396: [: 960: unary operator expected
/usr/bin/compiz-check: line 396: [: 1280: unary operator expected
           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2972 detected.

---

### Post by herbie643 on 2008-11-10
Theres a program called  compiz-check.  i  couldnt use compiz either.    compiz ran and asked if i wanted my graphics card removed from the blacklist.  i  did, and wham, compiz works great.
Perhaps that will help you out.

---

### Post by Magic_Spehar on 2008-11-10
> **herbie643 said:**
> Theres a program called  compiz-check.  i  couldnt use compiz either.    compiz ran and asked if i wanted my graphics card removed from the blacklist.  i  did, and wham, compiz works great.
Perhaps that will help you out.

Thanks for your reply Herbie. I did use compiz-check but after removing my card from the blacklist, I had to log out and then I got the message that my session was only possible in low resolution graphics.

---

### Post by oldsoundguy on 2008-11-10
Reading the plethora of posts concerning video card/chips and driver issues, it has become rather obvious that the new kernel in Intrepid does not play well with previous drivers and programs.  The issue is sufficient that the primary third party outfit for NVidia and ATI (Envy) has had to go to square one to even get displays to work at all.  Yet alone to work with all of the usual bells and whistles (which they do not YET).  When this will get resolved for all, unknown, as apparently this caught everyone by surprise.

---

### Post by herbie643 on 2008-11-10
I tend to agree with Oldsoundguy..  my video card failed at first on Hardy Heron after working on  Gutsy Gibbon..    Compiz-check got it working.  Now, I upgrade to Intrepid and everything works fine.  Of course my computer is 6 yrs old.   P4 with AT 9000 128mb ram.  On windows could go to resolution of 2048 x (i cant remember).  Here, just 1600x1200  and 24 bit instead of 32 bit color.   So it appears that video drivers are the biggest issues hitting Ubuntu and perhaps other distros as well.  Oh, and cant forget wireless networking.  I only hope they get it all figured out, because those 2 issues are big downsides.
Just my  opinion tho.

---


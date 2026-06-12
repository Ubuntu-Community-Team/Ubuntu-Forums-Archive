---
title: "Can't Use Desktop Effects"
date: 2008-09-01
forum: General Help
---

### Post by mikeMarek on 2008-09-01
When I try to use "normal" or "extra" effects, I get a message saying "Desktop effects could not be enabled". Compiz Fusion won't work either (I don't get an error message with Compiz, but they won't work). What's wrong here? I just got a new laptop and it is better than my old PC in every way possible, and my old PC ran Ubuntu and Compiz just fine.

Thanks for any help,
-Mike


[COLOR="Red"]EDIT:[/COLOR]

I ran the "Compiz Check" script, and here's what I got:

```

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

```

Any way I can change this? Can I re-install a dfferent driver? I've done that before in XP, not sure about Linux.


[COLOR="Red"]EDIT AGAIN:[/COLOR]

Apparently everything "works fine" when I ran the scipt again, but my PC restarted when I tried to put on "extra" effects.

---

### Post by CarlosNYB on 2008-09-01
Some graphics processors don't play well with linux, and the drivers aren't open source so it's not something linux developers can easily fix... I have that problem, personally.  My graphics is all fine, but I just can't get the 'effects' thingies working in gnome, although I can get transparency effects working great in Xfce, OpenBox, Fluxbox, etc.  Compiz and other things involve special uses of graphics processors, and driver issues can make it not work.

So, you may simply need to research the graphics processor on your laptop's motherboard and see if there is some program or script which will handle it's driver and make things work for linux, or whatever.  It may be you have one of the graphics processors on-board which baulks at some of the more intense/special graphics processing because of it's closed-source drivers, but on the other hand there may be some fix.  If you find out what your graphics processor is, that will help you research the issue or get help from someone on the forums.

---

### Post by hp owner on 2008-09-01
[LIST=1]
[/LIST]i have that same problem, so if you fix it, please let me know

---

### Post by mikeMarek on 2008-09-01
I managed to get everything working. There was a notification in the status bar and I clicked it and it let me install "restricted drivers" and that seemed to fix it.

Cheers,
-Mike

---

### Post by tuxxy on 2008-09-01
You could of installed the driver at system > admin > hardware drivers

---

### Post by hp owner on 2008-09-02
> **mikeMarek said:**
> When I try to use "normal" or "extra" effects, I get a message saying "Desktop effects could not be enabled". Compiz Fusion won't work either (I don't get an error message with Compiz, but they won't work). What's wrong here? I just got a new laptop and it is better than my old PC in every way possible, and my old PC ran Ubuntu and Compiz just fine.

Thanks for any help,
-Mike


[COLOR="Red"]EDIT:[/COLOR]

I ran the "Compiz Check" script, and here's what I got:

```

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

```

Any way I can change this? Can I re-install a dfferent driver? I've done that before in XP, not sure about Linux.


[COLOR="Red"]EDIT AGAIN:[/COLOR]

Apparently everything "works fine" when I ran the scipt again, but my PC restarted when I tried to put on "extra" effects.

i tied the compiz check script and got this, 
[CODE]
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

[\CODE]

can some one please help?

---


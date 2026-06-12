---
title: "Major ATI driver issue"
date: 2009-04-23
forum: Hardware
---

### Post by dE_logics on 2009-04-23
Going for an ATI seems to be one of the worst mistakes of my life...


I tried to improve the graphs performance (and some major issues with fullscreen drawing) by checking out this crap article - 

help.ubuntu.com/community/RadeonDriver

Which absolutely destroys the GUI taking me to the command line, so I reconfigure the xorg file, but after that it has ruined the performance completely...even the 2-d things are showing problems (like gnome with no effects) and extremely slow, furthermore the desktop effects are no longer getting enabled.

My card variant is the worst one...ATI x1270; we don't even have the drivers for windows in ati's site, forget linux. In fact ATI doesn't even know about this card (or atleast doesn't mention)...don't know how it got out of the R&D labs and got integrated in my pathetic dell lap.

Anyway...can someone help?

---

### Post by dE_logics on 2009-04-23
My GUI is broken...I'm working on a broken GUI PLEASE HELP!!](*,)

---

### Post by Bateluer on 2009-04-23
I became concerned when I saw this thread because I have a 4870 and intend to switch solely to Jaunty later today.

However, I am not familiar with the x1270. Is this a discrete ATI card? It sounds like an OEM only version of the Xpress X1250 line. 

ATI does have Linux drivers posted for the X1250 and Xpress 1250 products, which might work work your X1270. 

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English")

---

### Post by dE_logics on 2009-04-23
No its IGP.


THE PROBLEMS ARE GETTING WORST!!!...NOW MY TEXT COLOR IS WHITE!](*,)](*,)](*,)

No the x1200 drivers don't work...From the name it sounds like a over clocked x1250...but its drivers don't work.

I tied to improve the performance...and IT GOT WORST (I mentioned that)!!!


I really hate that page...it doesn't even have drivers for windows!...forget linux!

---

### Post by Bateluer on 2009-04-23
> **dE_logics said:**
> No its IGP.

I really hate that page...it doesn't even have drivers for windows!...forget linux!

Have you attempted using the RadeonHD driver? I wouldn't expect anything more than basic 2D rendering from a low end IGP though.

Have you looked at the site for your system's OEM builder to see if they've posted Linux drivers, doubt it, for that chip?

---

### Post by dE_logics on 2009-04-23
No I did not try the HD drivers...I thought they were for the HD seriese.


These graphs are made for aero...gnome effects and the simple GUI is a piecea cake.

P.S. Aero worked well on this card.

I'll give the HD drivers a try...

---

### Post by dE_logics on 2009-04-23
I reinstalled all opensource drivers...things are back to normal...and the HD drivers made things better!...thanks!

---

### Post by dE_logics on 2009-04-23
Any changes to that xorg.conf file crashes the whole GUI.

In [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/RadeonHD") link after configuring the xorg.conf as stated here (in that link) - 

```

Section "Device"
        ...     
        Driver   "radeonhd"
        Option   "DRI"
        Option   "AccelMethod"  "EXA"
EndSection
Section "DRI"
        Mode         0666
EndSection

```

On next reboot, there's no GUI...can someone point out the problem?

---

### Post by syxxness on 2009-04-23
> **dE_logics said:**
> 
Which absolutely destroys the GUI taking me to the command line, so I reconfigure the xorg file, but after that it has ruined the performance completely...even the 2-d things are showing problems (like gnome with no effects) and extremely slow, furthermore the desktop effects are no longer getting enabled.

I have an HD 4870, and I am having the exact same problems.  I downloaded the latest RC version (x64) on Tuesday and having updated to the official release yet.  I am not sure if there were any recent changes.

I was curious, would going back to the x86 version possibly fix this?

---

### Post by dE_logics on 2009-04-23
You don't have a problem :lolflag:

Download the proprietor drivers and install

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

If you're still in command line...try this - 

```

sudo dpkg-reinstall xserver-xorg

```

I'm too on x64.

---

### Post by dE_logics on 2009-04-23
Ok...change of issues........

On addition of 

```

Driver   "radeonhd"

```

in the device section of xorg.conf...videos dont play

Desktop effects don't get enabled.

---


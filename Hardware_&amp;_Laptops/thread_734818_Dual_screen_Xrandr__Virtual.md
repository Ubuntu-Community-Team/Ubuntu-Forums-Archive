---
title: "Dual screen Xrandr / Virtual"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by WardLoockx on 2008-03-25
I've upgrade to KDE4 now with hardy beta. 

The problem is that dual screen isn't working in KDE3 I did it with XrandR 
xrandr --output LVDS --left-of TMDS-1

The problem is that I needed to add virtual in the xorg.conf but now the xorg.conf looks different and the (sub)sections aren't there!  now I put it in like I think it is.can somebody help getting this think to work ? Really important

NOTE: the display subsections are added manual because they weren't there!

Here is my xorg.conf
> Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "be"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vmmouse"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"

        Subsection "Display"
                Depth 15
                Virtual 1650 1050
        EndSubsection

        Subsection "Display"
                Depth 15
        Virtual 1650 1050
    EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection

And here xrandr -q 

> LVDS connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      60.0*+
   1280x800       60.0
   1280x768       60.0
   1024x768       60.0
   800x600        60.3
   640x480        59.9
TMDS-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9
   1152x864       74.8
   1024x768       75.1     60.0
   800x600        75.0     60.3
   640x480        75.0     60.0
   720x400        70.1
TV disconnected (normal left inverted right x axis y axis)

Thanks!

---

### Post by WardLoockx on 2008-03-25
Maybe we should start with why the display sections aren't in the xorg.conf file?

---

### Post by pseudo-random on 2008-03-25
Not familiar with the Xrandr method.
I've found different ways of configuring my dual monitor setup by xorg.conf hacking with my old ATI ( in the days before the decent driver...shudder) and the nvidia GUI for my new card which is v.good.
I recommend trial and error with xorg. Grab some good ready made conf's with Google and extract whats relevant to your setup.
I daren't post mine incase it gets ridiculed. It works and I'm happy!

---

### Post by WardLoockx on 2008-03-25
Okay, I've changed the virtual screen to the right size... Now I have 2screens but the problem is that when I minimize a program and bring it up again I have a big grey area where the application should be. Anybody ?

---

### Post by alek01 on 2008-05-12
> **WardLoockx said:**
> Okay, I've changed the virtual screen to the right size... Now I have 2screens but the problem is that when I minimize a program and bring it up again I have a big grey area where the application should be. Anybody ?

Hi,
I have a VAIO FE890 (Intel 945) and just made a fresh install of Hardy because the upgrade messed things-up. On 7.10 the extended desktop worked fine but with Hardy when I add the Virtual line in a created subSection of Screen, the system boots on a GDM with only one screen and low resolution. Could you send me the exact xorg.conf you're using. FYI, mine is attached.
I thank you very much for your help as I can't find a solution after many hours of trying.
Thank you,

Alain

---


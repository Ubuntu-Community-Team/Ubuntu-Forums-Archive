---
title: "working xorg in Ubuntu 9.10 using Radeon driver on Radeon 9000?"
date: 2009-12-02
forum: Hardware
---

### Post by SeePU on 2009-12-02
I'm posting this to offer my experience on my trials of getting some 3D Desktop Effects working.  Some readers will recognize me as someone who has had major problems trying to enable 3D on my laptop.   Constant lockups, freezes and otherwise failures in getting 3D to be enabled, let alone work, provoked me to almost give up.

I sought a solution on the #kubuntu irc channel (as I usually use KDE) but I tried my latest experiment in live mode with my Ubuntu 9.10 Karmic Live CD.

I finally have some 3D working.  I needed to use EXA mode.  XAA mode would LOCK UP the laptop as before.   

Here are my hardware specs before I present the xorg.conf that 'worked' (I use that term with some reservation. ;-) ):
Thinkpad T41 model 2373-THD
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

Therefore, this potential solution is mostly applicable to a laptop's ATI card but it may work for other laptops with similar hardware.  It may also work for an equivalent desktop ATI card, YMMV.

Note, I only have *some* effects enabled.  No wobbly windows.  I also only recognize the window effects of it going 'blue' when moving the window.  I probably need further settings in xorg.cong to obtain more effects?  Or how do you do it in Gnome?  I only know of KDE 'Desktop Settings' that allows you to check the individual settings.

Okay, here is the xorg.conf file I created or edited:
Section "Device"
     Identifier      "Radeon 9000"
     Driver          "ati"
     BusID           "PCI:1:0:0"
     Option        "BusType" "PCI"
     Option         "AGPMode" "1"
     Option          "AccelMethod"   "EXA"
EndSection


Section "Monitor"
     Identifier      "InternalLCD"
     Option          "DPMS"
EndSection


Section "Screen"
     Identifier      "Default Screen"
     Device          "Radeon 9000"
     Monitor         "InternalLCD"
     DefaultDepth    24
     SubSection "Display"
             Depth           24
             Modes           "1440x900" "1024x768"
     EndSubSection
EndSection

Note, this is using the open source radeon driver.  It is NOT for the proprietary fglrx driver.   It may not work on cards that are newer or so far, mostly supported by the proprietary ATI driver.  It may work on older ATI Radeon cards that are only supported by the open source radeon driver.  YMMV.  I don't have all the effects enabled and perhaps enabling more effects would cause problems but at least, this appears to be some progress.

Thanks for reading and maybe it will help someone get further ahead as I was trying to do?

---

### Post by SeePU on 2009-12-03
No one is interested in this? :)

I thought it might confirm for some that you should first try EXA acceleration and not XAA.  :)

---


---
title: "Screen Resolution for ATI Mobility Radeon X200M"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by fwallace99 on 2007-03-22
Hi all --

I need help with my Toshiba Satellite A135-S2276. It uses an ATI Mobility Radeon X200M with shared (I know sigh) 128 MB of RAM.

My problem is my Dapper Drake install only goes to 1024X768 screen resolution, while the specs for Toshiba are 1280X800 (WXGA).

I don't need 3D acceleration or anything, just the higher resolution. I tried the Edgy Eft install and it sadly would not pick up my wireless card reliably while Dapper Drake did (PCMCIA card).

Reading through the forums I guess there are issues (to put it mildly) with the ATI cards, but I really want this to be a Linux only laptop. It came installed with Vista Home and the machine dragged like snail on acid.

Is it possible to just edit my /etc/X11/xorg.conf file:

...

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

...

And insert something to the native resolution or are special drivers needed etc?

Please let me know, and thanks.

---

### Post by vespo on 2007-03-23
Hi

Just insert "1280x800" in Modes line. You may need to restart X (Ctrl+Alt+Del) before it appears selectable in the Display Size preferences

---

### Post by fwallace99 on 2007-03-24
Thanks vespo but sadly no go :< .

I've inserted the following:

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
 SubSection "Display"
                Depth           8
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

But even after three reboots the System->Preferences->Screen Resolution only offers 1024x768, 800x600, and 640x480. Any suggestions? Maybe I'm missing something? I'll admit I'm not too used to tuning my Xorg configuration.

ETA: Feel stupid. Google is my friend. Apparently my Widescreen Laptop has a bug on install that's known for Ubuntu ... i.e. the resolution is not detected and it has to do with ATI drivers.

So following the advice:   sudo dpkg-reconfigure xserver-xorg

Well, everything worked after I pretty much followed the defaults. Very interesting.

Anyone care to comment about WHY it worked, what was going on there?

Here's the only difference I can see:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-50  <-- new
        VertRefresh     43-75 <-- new
EndSection

Weird huh?

But I love my widescreen. Looks so much nicer.

---


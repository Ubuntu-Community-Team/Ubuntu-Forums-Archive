---
title: "How to setup monitor with wrong default resolution using intel driver."
date: 2010-02-24
forum: Hardware
---

### Post by geoff123 on 2010-02-24
I just spent the last 2 hours figuring this one out so thought I'd share.  I've got this Samsung 24inch monitor - nice except it should run at 1920x1200 instead of 1680x1050 that it defaults to.  

I had to manually configure /etc/X11/xorg.confg to work with the i915 intel graphics... I hope this helps some one or gives some ideas.  Note that the Modeline can be determined from this command "cvt 1920 1200 60" or just use what I had. 

Make sure you do this after booting into a recovery console and use startx to tweak looking at the error messages.  If in doubt reboot.  

I could never get it to set up using xrandr alone.  Once I have this xorg.conf xrandr works nicely.  
------------

Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Samsung"
        ModelName      "SyncMaster245BW"
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 75.0
        Modeline "1920x1200"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
        Option   "DPI" "96 x 96"
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
                Modes "1920x1200" "1680x1050" "1600x1024" "1600x1200"
                Virtual 1920 1200
        EndSubSection
EndSection

Section "Device"
        Identifier     "videocard"
        Option          "DDC"           "false"
        Option "ModeDebug" "true"
        Option "LVDSFixedMode" "false"
        Driver "intel"  
EndSection
------------------------

---


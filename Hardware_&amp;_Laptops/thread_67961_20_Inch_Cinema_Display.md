---
title: "20 Inch Cinema Display"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by Studio A on 2005-09-21
I notice others with the same problem, but I can't find a solution.  Hoary 5.04 won't support my Cinema Display, the display goes to sleep.  I think Ubuntu is still launching as I can authenticate and tehn I hear the log in sounds.  Also my 17inch CRT ViewSonic works fine.  This is all on a Mac mini 1.42GHz, ATI Radeon 9200.

Thanks,

A

---

### Post by banadushi on 2005-09-21
Chances are that the resolution that the X server is trying to set is unsupported by the display.  Check the max supported resolution of the display and put it in your screen section.

For example my display maxes out at 1600x1200 so my screen section of /etc/X11/xorg.conf is:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI"
        Monitor         "CPD-G520"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

Have a good one!

Jason

---

### Post by Studio A on 2005-09-22
Thanks Jason!

I will try this today.  Admittedly, this is my first foray into Linux and I don't know the deal with /etc/X11/xorg.conf , but I think I can research it.

Thanks,

A

---


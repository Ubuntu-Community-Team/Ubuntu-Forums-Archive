---
title: "Resolution Problem"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by seiferkai on 2006-08-12
in windows i had my screen resolution 1280x1024
in ubuntu my resolution is on 1024x768

how can i make my resolution to 1280x1024 or bigger in ubuntu??

---

### Post by baldy1324 on 2006-08-12
type in
```
gksudo gedit /etc/X11/xorg.conf
``` terminal.
now scroll to the part that says Section "Screen". put 1024x768 before all the other resolutions. for example here is that section of my xorg.conf (i use 1280x1024 though)
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV35 [GeForce FX 5900XT]"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```

---

### Post by seiferkai on 2006-08-12
thanks for the info everything is peachy...

---

### Post by alb@nian on 2007-10-18
Thnx for this post, I had the same problem.

---


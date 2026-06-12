---
title: "Screen Resolution Toshiba"
date: 2009-05-13
forum: Hardware
---

### Post by chrismiceli on 2009-05-13
Hey,
I am trying to increase my screen resolution on my Toshiba Satellite A105-S4064 and I am unable to increase the screen resolution no matter what I do.  Here is my xorg.conf file
```

Section "Device"
   Identifier  "Configured Video Device"
EndSection

Section "Monitor"
   Identifier  "Configured Monitor"
   HorizSync 30-110
   VertRefresh 50-160
EndSection

Section "Screen"
   Identifier  "Default Screen"
   Monitor     "Configured Monitor"
   Device      "Configured Video Device"
   DefaultDepth 24
   SubSection  "Display"
      Depth 24
      Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "270x400" "640x480"
   EndSubSection
EndSection

```

But it seems to ignore this.  I'm not sure what to do now.

Thanks,
Michael

---


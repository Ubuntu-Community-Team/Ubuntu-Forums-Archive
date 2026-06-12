---
title: "MSI VR630 Strange Graphics related errors"
date: 2012-01-29
forum: Hardware
---

### Post by swimon on 2012-01-29
Hello,

I installed ubuntu 11.10 on my friends laptop (MSI VR630), because Windows failed to install. This laptop has the GeForce 9100M graphics chip onboard.

But I get these strange errors at startup:

```
Could not apply the stored configuration for monitors

none of the selected modes were compatible with the possible modes: 
Trying modes for CRTC 354 
CRTC 354: trying mode 1366x768@50Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 1360x768@51Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 1024x768@52Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 1024x768@53Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 960x540@54Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 840x525@55Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 832x624@56Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 800x600@57Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 800x600@58Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 800x600@59Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 800x600@60Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 800x600@61Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 800x512@62Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 720x450@63Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 720x400@64Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 700x525@65Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 680x384@66Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 680x384@67Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 640x512@68Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 640x512@69Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 640x480@70Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 640x480@71Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 640x480@72Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 640x480@73Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 640x480@74Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 640x400@75Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 640x350@76Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 576x432@77Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 576x432@78Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 576x432@79Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 576x432@80Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 576x432@81Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 576x432@82Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 576x432@83Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 512x384@84Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 512x384@85Hz with output at 1280x720@0Hz (pass 0) 
CRTC 354: trying mode 512x384@86Hz with output at 1280x720@0Hz (pass 0)
```

and everything looks "old"
[IMG]http://i39.tinypic.com/dp7nug.png[/IMG]

After I click on "ok" in the error message, most things like the top menubar changes back to the normal ubuntu theme, except for the file browser windows. They stay ugly.

How do I get rid of this message? I've tried all the "additional driver" options already...

Thanks in advance!

---

### Post by swimon on 2012-01-30
Fixed it myself,

found answer on this topic:
[http://forums.fedoraforum.org/showthread.php?t=256312](http://forums.fedoraforum.org/showthread.php?t=256312)

I removed ~/.config/monitors.xml and the error was gone...

---


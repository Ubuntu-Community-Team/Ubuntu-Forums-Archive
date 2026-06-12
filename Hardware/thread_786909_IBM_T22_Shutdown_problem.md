---
title: "IBM T22 Shutdown problem"
date: 2008-05-08
forum: Hardware
---

### Post by sassinak on 2008-05-08
I've got a T22 that has been giving me problems at shutdown since at least 7.10 if not 7.04, and the problem persists in 8.04 as well.  

When I shutdown I don't get the shutdown splash screen or text console that I can monitor, but the machine does close out of GNOME.  At this point the screen just goes blank (incorrect shutdown console size???), but even so, the shutdown process never seems to complete and the laptop never powers down.

General setup is T22->KVM->Dell 2208WFP 22" LCD

I had the same problems prior to the widescreen, and the problem happens even when not connected to the widescreen or the KVM.

Any ideas?

---

### Post by sassinak on 2008-06-11
Update for anyone searching about this problem: It's listed as a bug [#186056]("https://bugs.launchpad.net/ubuntu/+bug/186056/")

---

### Post by robaerus on 2008-11-14
Hello sassinak,
I think that is an issue regarding the video card: i had the same problem and after fixed my xorg.conf file i could shut my IBM T22 down without problems.
Try this: do a backup of your xorg.conf file, then replace the "device", "monitor" and "screen sections with this:

```
Section "Device"
Identifier "S3 Inc. 86C270-294 Savage/IX-MV"
Driver "savage"
BusID "PCI:1:0:0"
Option "BusType" "PCI"
Option "DmaMode" "None"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "S3 Inc. 86C270-294 Savage/IX-MV"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection
```

Hope this can help.
Cheers

---


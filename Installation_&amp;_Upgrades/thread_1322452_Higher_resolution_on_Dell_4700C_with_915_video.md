---
title: "Higher resolution on Dell 4700C with 915 video"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by alyster4k on 2009-11-10
A few hours of trial and error and I figured this out again after being stuck with 800x600 after a clean 9.10 install. I wanted to post this in case there were other people running into the same limited resolution on similar hardware such as mine and have to go the creation of xorg.conf route to fix. I found no direct answers but pieced this together through various posts and Google results.

FYI- This PC is a Dell 4700C with onboard Intel 915 video using a Dell 1704FPV monitor now running at 1280x1024 video resolution.
> 
#xorg.conf (X.Org X Window System server configuration file)

Section "Device"
    Identifier    "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
Identifier "DELL 1704FPV"
Horizsync	30.0-81.0
Vertrefresh	56.0-76.0
Option "DPMS"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Configured Video Device"
Monitor "DELL 1704FPV"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection


---

### Post by Mark Phelps on 2009-11-11
Since you have already set your default depth to 24, you don't need the other mode lines in the file. The one Display subsection for the depth of 24 should be sufficient.

---


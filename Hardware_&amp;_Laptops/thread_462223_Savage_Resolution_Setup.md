---
title: "Savage Resolution Setup"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by rapollon on 2007-06-02
Ah Ha!!! I'm not crazy, I've been tryig to set my 19" monitor to its recommended resolution...
Has anyone had any success with the S3 savage hardware?

My original post:

Re: HOWTO: change resolution/refresh rate in Xorg 

--------------------------------------------------------------------------------

I've been using various distos of debian for the last five years, but this one has me stumped. 
I have a 19" monitor, I want a 1280x1024 screen size. dpkg allowed me to get a giant screen area outside of view and that's with vesa. I get the size I'm little for it doesn't fit my screen. Monitor specs are: 1280x1024@75hz ; v:60.0 h:64.0 or v:75.03 h:80.0

I'm stuck in 1024x768

The microsoft users in my house are annoying me, one hiccup after five years worth of fixing their adawares and virus and windows boo boo's... 
I want silence again... Thanks!!!

here's my conf:


Section "Device"
Identifier "S3 Inc. 86C270-294 Savage/IX-MV"
Driver "savage"
BusID "PCI:1:1:0"
EndSection

Section "Monitor"
Identifier "synaps"
Option "DPMS"
Modeline "1280x1024@75" 156.43 1280 1312 1904 1936 1024 1043 1056 1076
HorizSync 80.8
VertRefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "S3 Inc. 86C270-294 Savage/IX-MV"
Monitor "synaps"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024_75"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024_75"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024_75"
EndSubSection
EndSection

---


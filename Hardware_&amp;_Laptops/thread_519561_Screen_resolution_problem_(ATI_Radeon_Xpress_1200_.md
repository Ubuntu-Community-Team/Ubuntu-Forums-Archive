---
title: "Screen resolution problem (ATI Radeon Xpress 1200 series)"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by Tynnhammar on 2007-08-07
Hey guys. I have a bit of a problem getting the resolution I want in in X-server. Atm I can only choose 1024*768 but I would like to have 1280*1024.

I have come to believe that this is due to a faulty xorg.conf (I've looked at other threads with people using similar cards). The problem I think is the HorizSync and VertRefresh values. They are currently: [PHP]HorizSync 30-70
VertRefresh  50-160[/PHP]

I have searched and looked through tons of websites trying to find the correct values, but I'm a bit lost. The computer I have is a HP Compaq 6715s.

[Here]("http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?contentType=SupportManual&lang=en&cc=se&docIndexId=691859&taskId=101&prodTypeId=321957&prodSeriesId=3368539#GotoTop") is the (messy) collection of manuals at HP.

Although I think this part is interesting [PHP]15.4-inch, WXGA display specifications
Metric U.S.
Dimensions
Height 20.7 cm 8.15 in
Width 33.1 cm 13.03 in
Diagonal 39.1 cm 15.39 in
Number of colors Up to 16.8 million
Contrast ratio 200:1 (typical)
Brightness 180 nits (typical)
Pixel resolution
Pitch 0.259 × 0.259 mm
Format 1440 × 900
Configuration RGB vertical stripe
Backlight CCFT
Character display 80 × 25
Total power consumption 6.5 W
Viewing angle +/-45° horizontal, +15/-35° vertical (typical)[/PHP]

and [PHP]15.4-inch, WSXGA display specifications
Metric U.S.
Dimensions
Height 20.7 cm 8.15 in
Width 33.1 cm 13.03 in
Diagonal 39.1 cm 15.39 in
Number of colors Up to 16.8 million
Contrast ratio 200:1 (typical)
Brightness 180 nits (typical)
Pixel resolution
Pitch 0.197 × 0.197 mm
Format 1680 × 1050
Configuration RGB vertical stripe
Backlight CCFT
Character display 80 × 25
Total power consumption 7.0 W
Viewing angle +/-40° horizontal, +/-50° vertical (typical)[/PHP]

Which I found at [http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01039189/c01039189.pdf](http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01039189/c01039189.pdf).

However, I have no idea how to parse anything useful out of it.

Please help :).

---

### Post by Tynnhammar on 2007-08-07
Bumpity.

---

### Post by Tynnhammar on 2007-08-07
Edit: NEVERMIND. I solved it :).

---

### Post by sputn1k on 2007-08-07
Hi

Your could try following settings in your /ect/X11/xorg.conf:

Section "Monitor"
Identifier "Syncmaster"
HorizSync 30.0 - 82.0
VertRefresh 50.0 - 85.0
Option "DPMS"
Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
Modeline "1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
DisplaySize 1440 900
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI-RadeonGPU"
Monitor "SyncMaster"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1440x900_60.00" "1440x900_70.00"
EndSubSection
EndSection

---

### Post by mk429 on 2007-10-20
I know this post is a bit old, but I have the exact same laptop (HP Compaq 6715s) and I can't get it to load X at all! I heard this was due to the graphics card and would be resolved in Gutsy, but I just downloaded Gutsy after months of waiting and it boots, but there's no X or Gnome! The screen flashes a few times and then stops, there are no error messages.. Could you possibly explain how you got your machine working with ubuntu? :(

---


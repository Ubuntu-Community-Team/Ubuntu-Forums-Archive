---
title: "specific resolution issue with ImageQuest (Hyundai) Q770 monitor"
date: 2008-08-21
forum: General Help
---

### Post by thabeatsociety on 2008-08-21
I've followed the following with no success:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Here's my monitor's specs:
[http://www.hyundaiq.com/pro_spec_q770.asp](http://www.hyundaiq.com/pro_spec_q770.asp)

I only get 800x600 and 640x480 resolutions in the drop down.

I'm assuming Hyundai bought or now owns ImageQuest, because nothing comes up for ImageQuest related to monitors when I search Google.

Here's the contents of my xorg.conf file:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
	HorizSync       30-70
        VertRefresh     50-150
SubSection      "Display"
        Depth   24
        Modes   "1024x768" "800x600" "640x480"
EndSubSection

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Generic Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Any advice? Downloadable Linux Ubuntu driver files?

I found the Graphics app in usr/share/applications - which mysteriously isn't listed under System > Administration where Screen is listed, but oh well - and although ImageQuest does come up, another model number in the 900's, not my Q770 comes up.  I tried the monitor listed even though it's a different model then mine, but that threw errors when I Ctrl+Alt+Backspace to log out and log back in.
:confused:

---

### Post by get2shashank on 2009-04-17
i too own that monitor.
and i have the problem that my computer doesn't goes forward after the login screen. it takes in my details and just sits there without working on anything. I am pretty sure that this is a monitor/graphics related problem.This is with ubuntu7.10.

more ever once when i was logged in(that was the first and last time i could get to my GUI desktop), although i set up the screen resolution at 1024x768, the osd menu of the monitor did not conform it. it rather said üser mode".

here is the link to my already posted problem.
[IMG]http://ubuntuforums.org/showthread.php?t=1128190[/IMG]

---


---
title: "How do I setup a 2nd Monitor?"
date: 2014-01-15
forum: Hardware
---

### Post by PopsTheSailor on 2014-01-15
Toshiba Satellite L655-S5150
Ubuntu 13.10
lspci | grep VGA = 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
Element Electronics ELET221 external monitor

I have a second monitor (Element Electronics) that I am using. It works but....

I plugged it into my laptop using a VGA cable. Ubuntu sees the monitor but in Display settings it shows a unknown. The problem I have is that the best resolution I can configure it to is 1024x768. The manual for the monitor says it will go all the way to 1920x1080. I would like to add additional resolution options for the monitor.

I've found posts that talk about adding a file called 10-monitor.conf to /usr/share/X11/xorg.conf.d but all the posts I have found talk about how to configure the file to add resolutions to the existing monitor. I need to know how to add the second monitor to this file. Here is what I have created so far but have not used it yet. Do I just add a "Monitor1" and "Screen1" sections with the resolution options I want??

Or, is this really the correct way to add additional resolution options to the second monitor?

Section "Monitor"
     Identifier "Monitor0"
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection
Section "Screen"
     Identifier "Screen0"
  Device "LVDS1"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1920x1080_60.00" "1024x768"
  EndSubSection
EndSection10-monitor.conf

---

### Post by PopsTheSailor on 2014-01-24
Bump

---

### Post by jp734 on 2014-01-25
Add horizsync and vertrefresh on your monitor section

Below is just an example. You will have to do some research for your monitor.
[COLOR=#0000cd][I]HorizSync 30-80
VertRefresh 30-80[/I][/COLOR]

---

### Post by PopsTheSailor on 2014-01-29
Marking this as solved. I wrote a script to set up the second monitor when I need it (don't use it all the time).

---


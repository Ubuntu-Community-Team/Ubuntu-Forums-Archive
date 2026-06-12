---
title: "X working in Live CD but not working when installed"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by mail2sona938 on 2005-06-27
I installed Ubuntu on my Compaq Laptop Presario M2000. The GUI is working when I installed in my laptop. I am a newbie and am extremely interested in taking out Windows from my system. Plz help.

---

### Post by Marc Higgins on 2005-06-27
you might try to reduce the resolution by editing;

/etc/X11/xorg.conf

hit esc on boot & enter rescue mode when it boots up

BACK IT UP FIRST
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

sudo nano /etc/X11/xorg.conf

find the section that looks like this;

Monitor "Generic Monitor"
DefaultDepth 24
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


see what yours is set to & try backing it off;

By reducing the "DefaultDepth" & the "Modes"

if it doesn;t work the best way may be to post your xorg.conf so eveyone can have a peek & give you advice.

By the way, if it does work also please let us know

---


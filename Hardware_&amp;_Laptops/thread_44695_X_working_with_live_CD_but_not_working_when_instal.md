---
title: "X working with live CD but not working when installed"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by mail2sona938 on 2005-06-27
X working with live CD but not working when installed. I can hear sounds but cannot see a thing when started. I am a newbie. I have a Compaq Presario M2000 laptop. Plz help

---

### Post by Marc Higgins on 2005-06-27
you might try to reduce the resolution by editing;

/etc/X11/xorg.conf

hit esc on boot & enter rescue mode when it boots up

BACK IT UP FIRST
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

sudo nano /etc/X11/xorg.conf

find the section that looks like this;

Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection


see what yours is set to & try backing it off;

By reducing the    "DefaultDepth"  & the "Modes"

if it doesn;t work the best way may be to post your xorg.conf so eveyone can have a peek & give you advice.

By the way, if it does work also please let us know

---

### Post by mail2sona938 on 2005-06-27
thanx...i use inel 915 chipset which I heard is not supported by intel drivers in ubuntu. So I tried using VESA driver..Now it works well....Thanks for ur help.....

---

### Post by turnip_flan on 2005-06-28
> thanx...i use inel 915 chipset which I heard is not supported by intel drivers in ubuntu. So I > tried using VESA driver..Now it works well

Hello,

I am having the same problem - work gave me a new dell 510 with the 915 chipset and I can't get ubuntu to work.

Anychance you could post how you got it use the Vesa driver - sorry this is probably a silly question but I miss my Ubuntu.  :cry: 

Cheers

Turnip

---

### Post by codejunkie on 2005-06-28
at the terminal login and type sudo nano /etc/X11/xorg.conf and find the section example: 
```
Driver      "nvidia"
``` replace whats listed here with vesa save and restart this should work.

---

### Post by turnip_flan on 2005-06-28
Thank you Codejunkie,

it worked perfectly

Am one happy person now

Turnip :)

---


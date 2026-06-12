---
title: "Connecting laptop to LCD TV using HDMI"
date: 2010-03-09
forum: Hardware
---

### Post by realn00b on 2010-03-09
Hi guyz,
    Here I am trying to connect my laptop to my LCD TV to view movies in better way! I bought this HDMi CABLE and plugged it in my laptop and at the back of my TV, but no output :(. I have tried different option on tv remote like HDMI1, HDMI2, PC, AV etc. But it just keeps searching.

M using ACER ASPIRE 4736Z.

---

### Post by jamfreak on 2010-03-09
connect your TV to your computer and type into a terminal the following command:
'xrandr --output TMDS-1 --auto'
you should see your computer screen on your TV after that. You still might have to adjust your resolution (System>Preferences>Display) ....I have to set mine to 1024x768
It that works you can just build a Launcher with those settings to automate

---

### Post by realn00b on 2010-03-09
I tried the command that you showed, but that didnt make any difference.

if i goto System > Preferences > Display, I see that my TV is getting detected there. I see 2 options, 1st laptop and 2nd name of my TV. When i Click on applu, it asks that if i want to keep the current config and i say yes. I tried different modes like AV, HDMI1, HDMI2 but it just keeps searching. I also tried different types of resolutions.
A
ny ideas?

---

### Post by jamfreak on 2010-03-09
what do you get if you just type 'xrandr' in your terminal? If your computer detects your TV you should get an output-----post it here

---

### Post by apolloltiujr on 2010-04-14
I found a website. Try if help

Linux Driver

[http://members.driverguide.com/index.php?action=wizard_step_1](http://members.driverguide.com/index.php?action=wizard_step_1)

---


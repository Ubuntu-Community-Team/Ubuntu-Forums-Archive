---
title: "NVIDIA 6150 not being recognized"
date: 2008-09-19
forum: Hardware
---

### Post by wyliga on 2008-09-19
Hey I've been running Hardy for about 6-7 months now with no major hickups. However yesterday I ran out of room on my ubuntu partition so I decided to just screw vista (sense it's had a virus for the past 3-4 months and been unusable anyway) and just go 100% Ubuntu.

Basically it didn't work. I first installed and was going through the basic things when I came to enabling my graphics card (NVIDIA geforce 6150). I rebooted and to my dismay ubuntu booted into limited graphics mode! I went to see what was up and everything seemed just fine. The driver said it was in use, and no other errors came up.

Obviously something is wrong. I've re-installed about half a dousen times so far to no avail. I even tried using envy. Envy installed a driver which I only assume is the correct one, but upon login I have no desktop. I see the Desktop background and I hear the greeting sound, but the panels/icons/everything else never shows up. I can't even use ctrl+alt+F1 to get into the terminal (however I can access the terminal before I log in).

I'm totally stuck and I have no idea what to do. I've tried envy and the regular ubuntu drivers (which say they support my card), but nothing seems to work. The only half solution I've found so far would be never even enabling the graphics drivers at all, but that would leave me with no desktop effects, and essentially no video card at all. Any insight as to what my problem is and how to fix it would be greatly appreciated. Thank you so much.

---

### Post by wyliga on 2008-09-21
Bump.
Long story short- Envy doesn't work. What else can I try?

---

### Post by overdrank on 2008-09-21
> **wyliga said:**
> Hey I've been running Hardy for about 6-7 months now with no major hickups. However yesterday I ran out of room on my ubuntu partition so I decided to just screw vista (sense it's had a virus for the past 3-4 months and been unusable anyway) and just go 100% Ubuntu.

Basically it didn't work. I first installed and was going through the basic things when I came to enabling my graphics card (NVIDIA geforce 6150). I rebooted and to my dismay ubuntu booted into limited graphics mode! I went to see what was up and everything seemed just fine. The driver said it was in use, and no other errors came up.

Obviously something is wrong. I've re-installed about half a dousen times so far to no avail. I even tried using envy. Envy installed a driver which I only assume is the correct one, but upon login I have no desktop. I see the Desktop background and I hear the greeting sound, but the panels/icons/everything else never shows up. I can't even use ctrl+alt+F1 to get into the terminal (however I can access the terminal before I log in).

I'm totally stuck and I have no idea what to do. I've tried envy and the regular ubuntu drivers (which say they support my card), but nothing seems to work. The only half solution I've found so far would be never even enabling the graphics drivers at all, but that would leave me with no desktop effects, and essentially no video card at all. Any insight as to what my problem is and how to fix it would be greatly appreciated. Thank you so much.

Hi and welcome, when you enable the drivers you may try and install nvidia settings to help with the resolution. You may also try and use the command ```
gksu displayconfig-gtk
``` and adjust your resolution there.

---

### Post by wyliga on 2008-09-21
Well I can't do that because I can't even access the terminal except by doing ctrl+alt+F1. But I do have an update.

When I log in I get an error it says something along the lines of:

"the panel encountered a problem with loading Gnome_panel_Trashapplet"

I'm not exactly sure what it says, because it flashes so quickly, but that's as much of it as I could get. I have no idea what that means or why I still can't see my desktop.

---


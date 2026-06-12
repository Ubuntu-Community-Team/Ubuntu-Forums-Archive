---
title: "[SOLVED] Lost LCD vid after kernel upgrade (2.6.24-21) Out of Range"
date: 2008-10-31
forum: Hardware
---

### Post by doas777 on 2008-10-31
Hello all,

I upgraded my kernel several days ago when 2.6.24-21 was released through the apt repos, and had a horrible time after rebooting. my monitor now blanks and the light blinks green (not orange like there's no signal) during non gui screens (at boot, and cntrl + alt + F1). it  shows the login window, and when I login to my desktop the screen blanks and says "Out of Range". most of the info online about this error message seems to only pertain to CRT monitors.

I restored my xorg.conf from backup, reinstalled nvidia-glx-new, and even changed out the video card, and dealt with parts of the problem (it was much worse beforehand), but I still cannot see VGA/gui-less screens, and it only shows a desktop at low res.

at this point i can get my monitor working at 800x600_56 (I know Refresh is meaningless on LCDs, but if I say 800x600_60 I get the out-of-range error), and it works, but I can't get it to go to 1024x768. the xorg.0.log shows that it has correctly detected my monitor (viewsonic VX922) and says it has a 400Mhz pixel clock and preferred res of 1280x1024.

I've started experimenting with VGA modes in my grub menu.lst, but at present, no love.

so I'm running out of ideas here. does anyone have any tips/tricks up their sleeves?

---

### Post by doas777 on 2008-11-02
well, I got it working, but there was so much fiddeling that I can't clearly describe the process.

I believe the elements that made the difference, were switching my VGA cable to DVI (fixed the VGA/low res screen issue),  setting nvidia-settings to load it's config at login (gksu nvidia-settings -l), and setting the gnome display res manager to 1024x768_60 to match the nvidia setting.

well, have fun folks,
Franklin

---


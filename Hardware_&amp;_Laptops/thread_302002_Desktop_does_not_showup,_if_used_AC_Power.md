---
title: "Desktop does not showup, if used AC Power"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by LinuxRush on 2006-11-18
I would like to know why my ubuntu system acts up, if I start my laptop with the power cable plugged in?

This is what happens: I start my laptop, select ubuntu - generic mode, then the splash screen comes up. Then, and I enter my username and password at the login screen, then gnome's dialog box starts (specifying what it's currently doing, i.e., loading Nautilus etc.) and then i see the wallpaper. THAT'S IT! NOTHING ELSE though :(

However, if I start my laptop without the power cable, everything works fine, gnome loads just fine!

What am I missing here? why such a weird problem?
Just to be sure: I rechecked my install CD for MD5 chcksum, and it checked out with no errors.

I am running Ubuntu along with windows XP Home Ed. (dual boot), my laptop is: HP Pavilion ZX5000 Series.

Any help would be great! if need more specs, let me know what exactly should I mention.

Thanks Guys,

-LR

---

### Post by LinuxRush on 2006-11-18
anyone with any suggestions/recommendations?

please help.

-LR

---

### Post by s_p_a_r_k_y on 2006-11-18
what happens if you take out the gnome-power-monitor from your gnome-panel?

---

### Post by LinuxRush on 2006-11-18
ok, can it be more wierd than this??

to try your suggestion, i removed the "battery" icon from the systray. and kept the power cord intact. and rebooted my machine. to my dismay, same thing happened. then i tried to  reboot without the powercord: SAME RESULT!!!! the gnome does not load at all! only the wallpaper appears. thats it!

Then i figured, lets disconnect the usb connection. this yielded same result. then i disconnected every wire (ethernet wire etc.) and rebooted. SAME RESULT!

so basically, my laptop does not load gnome (except for the wallpaper) when used in Generic mode.

please help.

-LR

---

### Post by s_p_a_r_k_y on 2006-11-18
i would think about nuking my gnome settings. perhaps you want to rename .gconf and .gconfd and .gnome2 and let gnome recreate those files.

---

### Post by LinuxRush on 2006-11-18
hi Sparky,

I found the source of the problem: it's GNOME!!!

I installed another desktop environment: KDE, and everything works PERFECTLY FINE! :)

I think I will stick to KDE now, since it does not screw up.... atleast it hasn't yet.

what could have been the problem?
-LR

---

